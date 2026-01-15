<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nano Banana Pro Generator</title>
    <script src="https://js.puter.com/v2/"></script>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 20px; background: #f0f4f8; }
        #prompt { width: 80%; padding: 12px; margin: 20px 0; font-size: 16px; }
        button { padding: 12px 24px; font-size: 18px; background: #4CAF50; color: white; border: none; cursor: pointer; }
        button:hover { background: #45a049; }
        #result { margin-top: 30px; max-width: 100%; }
        img { max-width: 100%; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.2); }
    </style>
</head>
<body>
    <h1>Nano Banana Pro (Gemini 3 Pro Image)</h1>
    <p>Введи промпт и нажми кнопку — получи крутую картинку бесплатно!</p>
    
    <input type="text" id="prompt" placeholder="Например: космический кот в стиле cyberpunk">
    <br>
    <button onclick="generate()">Сгенерировать 🍌✨</button>
    
    <div id="result"></div>

    <script>
        async function generate() {
            const prompt = document.getElementById('prompt').value.trim();
            if (!prompt) {
                alert("Напиши промпт!");
                return;
            }
            
            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = '<p>Генерирую... (20–90 сек) 🍌</p>';
            
            try {
                const img = await puter.ai.txt2img(prompt, {
                    model: "gemini-3-pro-image-preview"  // Nano Banana Pro
                });
                resultDiv.innerHTML = '';
                resultDiv.appendChild(img);
            } catch (error) {
                resultDiv.innerHTML = `<p style="color:red;">Ошибка: ${error.message}</p>`;
            }
        }
    </script>
</body>
</html>
