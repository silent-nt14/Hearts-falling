# Hearts-falling
Hearts falling from the sky
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>❤️ Falling Hearts ❤️</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            height: 100vh;
            overflow: hidden;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        .container {
            position: relative;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 10;
        }

        h1 {
            color: #fff;
            font-size: 3rem;
            text-shadow: 0 0 20px rgba(255, 107, 107, 0.8);
            animation: pulse 2s ease-in-out infinite;
            margin-bottom: 20px;
            text-align: center;
        }

        .message {
            color: #ffb6c1;
            font-size: 1.5rem;
            text-align: center;
            max-width: 80%;
            line-height: 1.6;
            animation: fadeIn 3s ease-in;
        }

        .heart {
            position: fixed;
            top: -50px;
            font-size: 20px;
            animation: fall linear infinite;
            pointer-events: none;
            z-index: 1;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .floating {
            position: absolute;
            font-size: 30px;
            animation: float 6s ease-in-out infinite;
            opacity: 0.6;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-30px) rotate(10deg); }
        }

        .btn {
            margin-top: 30px;
            padding: 15px 40px;
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            border: none;
            border-radius: 50px;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
            box-shadow: 0 10px 30px rgba(255, 107, 107, 0.4);
            transition: all 0.3s ease;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .btn:hover {
            transform: scale(1.1);
            box-shadow: 0 15px 40px rgba(255, 107, 107, 0.6);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>❤️ For You ❤️</h1>
        <div class="message">
            Sending you lots of love and positive vibes! <br>
            May your day be filled with joy and happiness! 🌟
        </div>
        <button class="btn" onclick="createBurst()">Click for More Love! 💕</button>
    </div>

    <script>
        const heartEmojis = ['❤️', '💖', '💗', '💓', '💝', '💕', '💘', '💞', '💟', '❣️'];
        const colors = ['#ff6b6b', '#feca57', '#ff9ff3', '#54a0ff', '#5f27cd', '#00d2d3'];

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 3 + 2 + 's';
            heart.style.fontSize = Math.random() * 30 + 15 + 'px';
            heart.style.opacity = Math.random() * 0.5 + 0.5;
            
            document.body.appendChild(heart);
            
            setTimeout(() => {
                heart.remove();
            }, 5000);
        }

        function createBurst() {
            for (let i = 0; i < 20; i++) {
                setTimeout(createHeart, i * 100);
            }
        }

        // Create hearts continuously
        setInterval(createHeart, 300);

        // Create floating background hearts
        function createFloatingHeart() {
            const heart = document.createElement('div');
            heart.classList.add('floating');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.top = Math.random() * 100 + 'vh';
            heart.style.animationDelay = Math.random() * 5 + 's';
            heart.style.color = colors[Math.floor(Math.random() * colors.length)];
            document.body.appendChild(heart);
        }

        for (let i = 0; i < 10; i++) {
            createFloatingHeart();
        }
    </script>
</body>
</html>
