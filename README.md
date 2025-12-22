# -the-games-club-
A web where people can play mini games in free times and enjoy and pass times in free time games will be normal and kids friendly 
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>The Games Club</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #1d2671, #c33764);
      color: #fff;
      text-align: center;
    }
    header {
      padding: 20px;
      background: rgba(0,0,0,0.4);
    }
    header h1 {
      margin: 0;
      font-size: 2.5rem;
    }
    nav {
      margin-top: 10px;
    }
    nav button {
      padding: 10px 20px;
      margin: 5px;
      border: none;
      border-radius: 20px;
      cursor: pointer;
      font-size: 1rem;
    }
    nav button:hover {
      opacity: 0.8;
    }
    .container {
      padding: 30px;
    }
    .games {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
      margin-top: 30px;
    }
    .game-card {
      background: rgba(255,255,255,0.15);
      border-radius: 20px;
      padding: 20px;
      cursor: pointer;
      transition: transform 0.2s, background 0.2s;
    }
    .game-card:hover {
      transform: scale(1.05);
      background: rgba(255,255,255,0.25);
    }
    footer {
      margin-top: 40px;
      padding: 10px;
      font-size: 0.9rem;
      background: rgba(0,0,0,0.3);
    }
    /* Game area */
    #gameArea {
      display: none;
      margin-top: 20px;
    }
    canvas {
      background: #87ceeb;
      border-radius: 10px;
      margin-top: 10px;
    }
  </style>
</head>
<body>  <header>
    <h1>🎮 The Games Club</h1>
    <p>Fun & Kid-Friendly Mini Games</p>
    <nav>
      <button onclick="goHome()">Home</button>
    </nav>
  </header>  <div class="container" id="home">
    <h2>Select a Game</h2>
    <div class="games">
      <div class="game-card" onclick="startGame('flappy')">
        🐦<br><b>Flappy Bird</b>
        <p>Tap to fly and avoid pipes</p>
      </div>
      <div class="game-card" onclick="startGame('fruit')">
        🍉<br><b>Fruit Ninja</b>
        <p>Slice the fruits</p>
      </div>
      <div class="game-card" onclick="startGame('archery')">
        🎯<br><b>Archery</b>
        <p>Aim and hit the target</p>
      </div>
      <div class="game-card" onclick="startGame('shooting')">
        🔫<br><b>Shooting</b>
        <p>Hit moving objects</p>
      </div>
    </div>
  </div>  <div class="container" id="gameArea">
    <h2 id="gameTitle"></h2>
    <p id="gameInfo"></p>
    <canvas id="gameCanvas" width="300" height="400"></canvas>
  </div>  <footer>
    © 2025 The Games Club | Play • Learn • Enjoy
  </footer>  <script>
    const home = document.getElementById('home');
    const gameArea = document.getElementById('gameArea');
    const gameTitle = document.getElementById('gameTitle');
    const gameInfo = document.getElementById('gameInfo');
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    function goHome() {
      gameArea.style.display = 'none';
      home.style.display = 'block';
      ctx.clearRect(0, 0, canvas.width, canvas.height);
    }

    function startGame(game) {
      home.style.display = 'none';
      gameArea.style.display = 'block';

      if (game === 'flappy') {
        gameTitle.innerText = '🐦 Flappy Bird (Demo)';
        gameInfo.innerText = 'Click to make the bird fly';
        flappyBird();
      } else if (game === 'fruit') {
        gameTitle.innerText = '🍉 Fruit Ninja (Demo)';
        gameInfo.innerText = 'Click on fruits to slice them';
        fruitNinja();
      } else if (game === 'archery') {
        gameTitle.innerText = '🎯 Archery (Demo)';
        gameInfo.innerText = 'Click to shoot arrow at target';
        archeryGame();
      } else if (game === 'shooting') {
        gameTitle.innerText = '🔫 Shooting (Demo)';
        gameInfo.innerText = 'Click to shoot moving targets';
        shootingGame();
      }
    }

    /* Simple demo games */

    function flappyBird() {
      let y = 200;
      canvas.onclick = () => y -= 30;
      setInterval(() => {
        ctx.clearRect(0,0,300,400);
        y += 2;
        ctx.fillStyle = 'yellow';
        ctx.beginPath();
        ctx.arc(150, y, 15, 0, Math.PI * 2);
        ctx.fill();
      }, 30);
    }

    function fruitNinja() {
      let x = 150, y = 400;
      canvas.onclick = () => y = 100;
      setInterval(() => {
        ctx.clearRect(0,0,300,400);
        y += 3;
        if (y > 400) y = 0;
        ctx.fillStyle = 'red';
        ctx.beginPath();
        ctx.arc(x, y, 20, 0, Math.PI * 2);
        ctx.fill();
      }, 40);
    }

    function archeryGame() {
      canvas.onclick = () => {
        ctx.clearRect(0,0,300,400);
        ctx.fillStyle = 'green';
        ctx.fillRect(130, 50, 40, 40);
        ctx.strokeStyle = 'white';
        ctx.beginPath();
        ctx.moveTo(150, 350);
        ctx.lineTo(150, 70);
        ctx.stroke();
      };
    }

    function shootingGame() {
      let x = 0;
      setInterval(() => {
        ctx.clearRect(0,0,300,400);
        x += 3;
        if (x > 300) x = 0;
        ctx.fillStyle = 'orange';
        ctx.fillRect(x, 150, 30, 30);
      }, 30);
    }
  </script></body>
</html>
