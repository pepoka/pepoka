- 👋 Hi, I’m @pepoka
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!DOCTYPE html>
<html>
<head>
  <title>Dino Game</title>
  <style>
    canvas {
      border: 1px solid black;
    }
  </style>
</head>
<body>
  <canvas id="gameCanvas" width="480" height="270"></canvas>
  <script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    const groundY = canvas.height - 10;
    const dino = {
      x: 50,
      y: groundY - 40,
      width: 40,
      height: 40,
      velocityY: 0,
      gravity: 1.5,
      jumpVelocity: -20,
      isJumping: false,
      isDead: false,
      draw: function () {
        ctx.fillStyle = 'green';
        ctx.fillRect(this.x, this.y, this.width, this.height);
      },
      update: function () {
        if (this.isJumping) {
          this.velocityY += this.gravity;
          this.y += this.velocityY;

          if (this.y > groundY - this.height) {
            this.y = groundY - this.height;
            this.isJumping = false;
          }
        }
      },
      jump: function () {
        if (!this.isJumping) {
          this.velocityY = this.jumpVelocity;
          this.isJumping = true;
        }
      },
      die: function () {
        this.isDead = true;
      }
    };

    function draw() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      dino.draw();
    }

    function update() {
      dino.update();
    }

    function gameLoop() {
      update();
      draw();
      requestAnimationFrame(gameLoop);
    }

    gameLoop();

    window.addEventListener('keydown', (event) => {
      if (event.code === 'Space' && !dino.isDead) {
        dino.jump();
      }
    });
  </script>
</body>
</html><!---
pepoka/pepoka is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
