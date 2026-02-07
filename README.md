<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #ffeef2;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            text-align: center;
        }

        #container {
            z-index: 10;
            background: white;
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }

        h1 {
            color: #d63384;
            font-size: 2.5rem;
        }

        .buttons {
            margin-top: 20px;
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        button {
            padding: 15px 30px;
            font-size: 1.2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.2s;
        }

        #yesBtn {
            background-color: #ff4d6d;
            color: white;
        }

        #noBtn {
            background-color: #6c757d;
            color: white;
            position: relative;
        }

        /* Balloon Styling */
        .balloon {
            position: absolute;
            font-size: 2rem;
            user-select: none;
            pointer-events: none;
            z-index: 1;
        }

        /* Success Message Styling */
        #message {
            display: none;
        }
    </style>
</head>
<body>

    <div id="container">
        <div id="askSection">
            <h1>Will you be my Valentine? ❤️</h1>
            <div class="buttons">
                <button id="yesBtn" onclick="showSuccess()">Yes</button>
                <button id="noBtn" onmouseover="moveButton()">No</button>
            </div>
        </div>

        <div id="message">
            <h1>I knew you would say yes! 🥰</h1>
            <p style="font-size: 1.2rem; color: #555;">
                I'll meet you today at <strong>[Insert Hotel Name]</strong> <br> 
                around <strong>[Insert Time]</strong>.
            </p>
            <div style="font-size: 3rem;">💖</div>
        </div>
    </div>

    <script>
        // Move the "No" button when hovered
        function moveButton() {
            const btn = document.getElementById('noBtn');
            const x = Math.random() * (window.innerWidth - btn.offsetWidth);
            const y = Math.random() * (window.innerHeight - btn.offsetHeight);
            
            btn.style.position = 'absolute';
            btn.style.left = x + 'px';
            btn.style.top = y + 'px';
        }

        // Show the success message
        function showSuccess() {
            document.getElementById('askSection').style.display = 'none';
            document.getElementById('message').style.display = 'block';
            // Stop balloons or add more? Let's just let them keep floating!
        }

        // Create floating heart balloons
        function createBalloon() {
            const balloon = document.createElement('div');
            balloon.className = 'balloon';
            balloon.innerHTML = '🎈❤️';
            balloon.style.left = Math.random() * 100 + 'vw';
            balloon.style.bottom = '-50px';
            balloon.style.opacity = Math.random() * 0.5 + 0.5;
            
            // Random duration for floating up
            const duration = Math.random() * 5 + 5;
            balloon.style.transition = `transform ${duration}s linear, opacity ${duration}s`;
            
            document.body.appendChild(balloon);

            // Animate up
            setTimeout(() => {
                balloon.style.transform = `translateY(-${window.innerHeight + 100}px) rotate(${Math.random() * 40 - 20}deg)`;
            }, 100);

            // Remove from DOM after animation
            setTimeout(() => {
                balloon.remove();
            }, duration * 1000);
        }

        // Generate balloons every second
        setInterval(createBalloon, 800);
    </script>
</body>
</html>
