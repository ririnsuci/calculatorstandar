<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kalkulator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
            position: relative;
        }
        .calculator {
            width: 300px;
            background: #92cae4;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }
        .display {
            width: 100%;
            height: 50px;
            text-align: right;
            font-size: 1.5em;
            margin-bottom: 10px;
            padding: 5px;
            border: none;
            background: #eeeeee;
            border-radius: 5px;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 5px;
        }
        button {
            width: 100%;
            height: 50px;
            font-size: 1.2em;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .operator { background: #ff9500; color: white; }
        .clear { background: #ff3b30; color: white; }
        .equal { background: #4cd964; color: white; }
        .number, .decimal, .negate { background: #ddd; }
    </style>
</head>
<body>
    <h1 style="color: #007bff; margin-bottom: 10px;">calculatorstandar</h1>
    <div class="calculator">
        <input type="text" class="display" id="display" disabled>
        <div class="buttons">
            <button class="clear" onclick="clearDisplay()">C</button>
            <button onclick="appendValue('%')">%</button>
            <button onclick="negate()">+/-</button>
            <button class="operator" onclick="appendValue('/')">&divide;</button>
            <button class="number" onclick="appendValue('7')">7</button>
            <button class="number" onclick="appendValue('8')">8</button>
            <button class="number" onclick="appendValue('9')">9</button>
            <button class="operator" onclick="appendValue('*')">x</button>
            <button class="number" onclick="appendValue('4')">4</button>
            <button class="number" onclick="appendValue('5')">5</button>
            <button class="number" onclick="appendValue('6')">6</button>
            <button class="operator" onclick="appendValue('-')">-</button>
            <button class="number" onclick="appendValue('1')">1</button>
            <button class="number" onclick="appendValue('2')">2</button>
            <button class="number" onclick="appendValue('3')">3</button>
            <button class="operator" onclick="appendValue('+')">+</button>
            <button class="number" onclick="appendValue('0')">0</button>
            <button class="decimal" onclick="appendValue('.')">.</button>
            <button class="equal" onclick="calculate()">=</button>
        </div>
    </div>
    <script>
        function appendValue(value) {
            document.getElementById("display").value += value;
        }
        function clearDisplay() {
            document.getElementById("display").value = "";
        }
        function calculate() {
            try {
                let expression = document.getElementById("display").value;
                expression = expression.replace('%', '/100');
                document.getElementById("display").value = new Function('return ' + expression)();
            } catch {
                document.getElementById("display").value = "Error";
            }
        }
        function negate() {
            let display = document.getElementById("display");
            if (display.value) {
                display.value = display.value.startsWith('-') ? display.value.substring(1) : '-' + display.value;
            }
        }
    </script>
</body>
</html>
