<!EMISSORA MAPIM WebRadio - MATO GROSSO
Criador - Allisson Carfi ( popotocba )
! Todos os Direitos reservados 2014 - 2025 >

<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MAPIM Web Rádio - Ao Vivo com Chat</title>
  <style>
    /* Estilo básico do corpo */
    body {
      background: linear-gradient(135deg, #ff0000, #ff9800);
      font-family: Arial, sans-serif;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      color: #FFF;
    }

    /* Container principal com efeito neon */
    .container {
      background: #1a1a1a;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0px 0px 20px rgba(255, 0, 0, 0.7), 0px 0px 30px rgba(255, 87, 34, 0.5);
      max-width: 500px;
      width: 90%;
      color: #FFF;
      text-align: center;
      display: flex;
      flex-direction: column;
      gap: 20px;
    }

    /* Título da Rádio */
    .container h1 {
      font-size: 1.8em;
      color: #ff9800;
      margin-bottom: 20px;
      text-shadow: 0px 0px 10px rgba(255, 87, 34, 0.8);
    }

    /* Exibição do título da música */
    .current-song {
      background: linear-gradient(45deg, #ff5722, #ff9800);
      padding: 10px;
      border-radius: 8px;
      font-size: 1.1em;
      font-weight: bold;
      color: #1a1a1a;
    }

    /* Estilos do áudio */
    audio {
      width: 100%;
      border-radius: 10px;
    }

    /* Container do chat */
    .chat-container {
      width: 100%;
      height: 300px;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0px 0px 10px rgba(255, 0, 0, 0.5), 0px 0px 20px rgba(255, 87, 34, 0.3);
    }
  </style>
</head>
<body>
  <!-- Container principal com player, título da música e chat -->
  <div class="container">
    <!-- Imagem do Logotipo -->
  <div align="center">
    <img src="https://mapim.home.blog/wp-content/uploads/2024/11/logo-removebg-preview-1.png" alt="SmartTV" width="440" height="349">
  </div>
    <!-- Player de áudio -->
    <audio id="audioPlayer" controls autoplay src="https://stream.zeno.fm/7wbprc3ce4qvv?"></audio>
    <!-- Exibição do título da música -->
    <div class="current-song" id="current-song">Carregando...</div>
    <div align="center">
    <img src="https://mapim.home.blog/wp-content/uploads/2024/09/mapim-banner-1-1.gif" alt="SmartTV" width="487" height="95">
  </div>
    <!-- Container do chat -->
    <div class="chat-container">
      <iframe src="https://www3.cbox.ws/box/?boxid=3528213&boxtag=YcxjSO" width="100%" height="100%" allowtransparency="yes" allow="autoplay" frameborder="0" marginheight="0" marginwidth="0" scrolling="auto"></iframe>
    </div>
 
  </div>

  <script>
    // Função para inicializar o EventSource e receber o título da música
    function startMusicStream() {
      const eventSource = new EventSource("https://api.zeno.fm/mounts/metadata/subscribe/7wbprc3ce4qvv");

      eventSource.addEventListener("message", (event) => {
        try {
          const data = JSON.parse(event.data);
          const songTitle = data.streamTitle || "MAPIM WebRádio";
          document.getElementById("current-song").textContent = ` ${songTitle}`;
        } catch (error) {
          console.error("Erro ao processar dados da música:", error);
        }
      });
      eventSource.addEventListener("error", (error) => {
        console.error("Erro no stream de música:", error);
      });
    }

    // Chama a função para iniciar a escuta do stream de música
    startMusicStream();
  </script>
</body>
</html>
