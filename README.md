# barisalimmii
<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <title>Barışalım mı?</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      text-align: center;
      margin: 0;
      background-color: #f8f8f8;
      overflow: hidden;
    }

    h1 {
      font-size: 3em;
      color: #333;
      margin-top: 100px;
    }

    .btn {
      font-size: 1.5em;
      padding: 10px 20px;
      margin: 20px;
      cursor: pointer;
      border: none;
      border-radius: 10px;
      position: relative;
      z-index: 1;
    }

    #evetBtn {
      background-color: #4CAF50;
      color: white;
    }

    #hayirBtn {
      background-color: #d9534f;
      color: white;
      position: absolute;
      top: 300px;
      left: 50%;
      transition: top 0.3s ease, left 0.3s ease;
    }

    #message {
      display: none;
      font-size: 2em;
      color: #fff;
      margin-top: 50px;
      z-index: 2;
      position: relative;
    }

    .heart {
      position: absolute;
      color: red;
      font-size: 2em;
      animation: float 4s linear infinite;
      opacity: 0.8;
      pointer-events: none;
    }

    @keyframes float {
      0% {
        transform: translateY(0) scale(1);
        opacity: 1;
      }
      100% {
        transform: translateY(-800px) scale(1.5);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <h1 id="title">Barışalım mı?</h1>
  <button id="evetBtn" class="btn">Evet</button>
  <button id="hayirBtn" class="btn">Hayır</button>
  <div id="message">Her şey için özür dilerim.<br>Barışmak istiyorum.<br>Seni çok seviyorum ❤️</div>

  <script>
    const evetBtn = document.getElementById("evetBtn");
    const hayirBtn = document.getElementById("hayirBtn");
    const title = document.getElementById("title");
    const message = document.getElementById("message");
    let evetBasildi = false;

    // Kaçan hayır butonu
    hayirBtn.addEventListener("mouseover", () => {
      if (!evetBasildi) {
        const maxX = window.innerWidth - 100;
        const maxY = window.innerHeight - 100;
        const randomX = Math.floor(Math.random() * maxX);
        const randomY = Math.floor(Math.random() * maxY);
        hayirBtn.style.left = randomX + "px";
        hayirBtn.style.top = randomY + "px";
      }
    });

    evetBtn.addEventListener("click", () => {
      evetBasildi = true;

      // Arka plan değişsin
      document.body.style.background = "linear-gradient(to bottom, #ff9aa2, #ffdde1)";

      // Başlık ve butonları gizle
      title.style.display = "none";
      evetBtn.style.display = "none";
      hayirBtn.style.display = "none";

      // Mesaj göster
      message.style.display = "block";

      // Kalpleri oluştur
      for (let i = 0; i < 50; i++) {
        const heart = document.createElement("div");
        heart.classList.add("heart");
        heart.style.left = Math.random() * window.innerWidth + "px";
        heart.style.top = Math.random() * window.innerHeight + "px";
        heart.innerHTML = "❤️";
        heart.style.fontSize = `${Math.random() * 20 + 20}px`;
        document.body.appendChild(heart);
      }
    });
  </script>
</body>
</html>
