<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Calculadora de Derivadas Directas</title>
<style>
    body {
        font-family: Arial, sans-serif;
        text-align: center;
        margin-top: 50px;
        background-color: #f4f4f4;
    }

    .container {
        background: white;
        padding: 20px;
        border-radius: 10px;
        width: 400px;
        margin: auto;
        box-shadow: 0 0 10px rgba(0,0,0,0.2);
    }

    input, button {
        padding: 10px;
        margin: 10px;
        width: 90%;
    }

    #resultado {
        font-size: 18px;
        font-weight: bold;
        color: #0066cc;
    }
</style>
</head>
<body>

<div class="container">
    <h2>Calculadora de Derivadas Directas</h2>
    <p>Ingresa un término tipo: 3x^2, 5x^4, -2x^3</p>

    <input type="text" id="funcion" placeholder="Ejemplo: 3x^2">
    <button onclick="derivar()">Derivar</button>

    <p id="resultado"></p>
</div>

<script>
function derivar() {
    const expresion = document.getElementById("funcion").value.trim();

    const regex = /^(-?\d*)x\^(\d+)$/;
    const match = expresion.match(regex);

    if (!match) {
        document.getElementById("resultado").innerText =
            "Formato no válido. Usa algo como 3x^2";
        return;
    }

    let coef = match[1];
    let exponente = parseInt(match[2]);

    if (coef === "" || coef === "+") coef = 1;
    else if (coef === "-") coef = -1;
    else coef = parseInt(coef);

    const nuevoCoef = coef * exponente;
    const nuevoExp = exponente - 1;

    let derivada;

    if (nuevoExp === 0) {
        derivada = `${nuevoCoef}`;
    } else if (nuevoExp === 1) {
        derivada = `${nuevoCoef}x`;
    } else {
        derivada = `${nuevoCoef}x^${nuevoExp}`;
    }

    document.getElementById("resultado").innerText =
        `Derivada: ${derivada}`;
}
</script>

</body>
</html> 
