* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

body {
  background-color: #0f172a;
  color: #f8fafc;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

header {
  width: 100%;
  max-width: 600px;
  margin-bottom: 24px;
  text-align: center;
}

h1 {
  font-size: 1.8rem;
  margin-bottom: 16px;
  color: #38bdf8;
}

#search {
  width: 100%;
  padding: 12px 16px;
  border-radius: 8px;
  border: 1px solid #334155;
  background-color: #1e293b;
  color: #fff;
  font-size: 1rem;
  outline: none;
}

#search:focus {
  border-color: #38bdf8;
}

main {
  width: 100%;
  max-width: 600px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.card {
  background-color: #1e293b;
  border: 1px solid #334155;
  border-radius: 12px;
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.card-header {
  display: flex;
  align-items: center;
  gap: 10px;
}

.tag {
  background-color: #334155;
  color: #94a3b8;
  font-size: 0.75rem;
  padding: 4px 8px;
  border-radius: 6px;
  font-weight: bold;
}

.tag.destaque {
  background-color: #0284c7;
  color: #fff;
}

.card h3 {
  font-size: 1.2rem;
}

.description {
  color: #94a3b8;
  font-size: 0.9rem;
}

.code-box {
  background-color: #0f172a;
  padding: 10px;
  border-radius: 6px;
  font-family: monospace;
  font-size: 0.85rem;
  color: #38bdf8;
  overflow-x: auto;
}

.btn-copy {
  background-color: #38bdf8;
  color: #0f172a;
  border: none;
  padding: 10px;
  border-radius: 6px;
  font-weight: bold;
  font-size: 0.9rem;
  cursor: pointer;
  transition: opacity 0.2s;
}

.btn-copy:active {
  opacity: 0.8;
}
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Diretório de Conteúdo</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <header>
    <h1>Meu Diretório</h1>
    <input type="text" id="search" placeholder="Pesquisar itens...">
  </header>

  <main id="cards-container">
    <!-- Card 1 -->
    <div class="card">
      <div class="card-header">
        <span class="tag">Novo</span>
        <h3>Item Exemplo 1</h3>
      </div>
      <p class="description">Descrição rápida do conteúdo ou do recurso que está sendo compartilhado aqui.</p>
      <div class="code-box">
        <code>código ou texto do item 1...</code>
      </div>
      <button class="btn-copy" onclick="copiar(this)">Copiar Conteúdo</button>
    </div>

    <!-- Card 2 -->
    <div class="card">
      <div class="card-header">
        <span class="tag destaque">Destaque</span>
        <h3>Item Exemplo 2</h3>
      </div>
      <p class="description">Outra descrição detalhada para explicar do que se trata este segundo item.</p>
      <div class="code-box">
        <code>código ou texto do item 2...</code>
      </div>
      <button class="btn-copy" onclick="copiar(this)">Copiar Conteúdo</button>
    </div>
  </main>

  <script src="script.js"></script>
</body>
</html>
// Função para copiar o texto do bloco correspondente
function copiar(botao) {
  const card = botao.parentElement;
  const texto = card.querySelector('code').innerText;

  navigator.clipboard.writeText(texto).then(() => {
    const textoOriginal = botao.innerText;
    botao.innerText = "Copiado! ✓";
    botao.style.backgroundColor = "#22c55e";

    setTimeout(() => {
      botao.innerText = textoOriginal;
      botao.style.backgroundColor = "#38bdf8";
    }, 2000);
  });
}

// Lógica de busca rápida
document.getElementById('search').addEventListener('input', function(e) {
  const termo = e.target.value.toLowerCase();
  const cards = document.querySelectorAll('.card');

  cards.forEach(card => {
    const conteudo = card.innerText.toLowerCase();
    if (conteudo.includes(termo)) {
      card.style.display = 'flex';
    } else {
      card.style.display = 'none';
    }
  });
});

