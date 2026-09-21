# Dourê — Projeto de marca

Três páginas HTML autocontidas (sem build, sem dependências para instalar — abrem direto no navegador ou num live server do Cursor/VS Code).

## Arquivos

- **`index.html`** — Site institucional da marca (hero, coleção, presentes, experiência, empresas, contato).
- **`precificacao.html`** — Simulador de custo, preço e margem por canal (iFood, site, WhatsApp, retirada). Parâmetros editáveis, salvos no `localStorage` do navegador.
- **`playbook.html`** — Documento estratégico completo: naming, slogans, posicionamento, catálogo, calendário comercial, 100 posts, 30 Reels, modelo de dados, franchise readiness.

## Como abrir

Não precisa de `npm install` nem servidor. Duas opções:

1. Abra o arquivo direto no navegador (duplo clique ou `Ctrl+O`).
2. Ou, no Cursor, use a extensão **Live Server** (clique direito no arquivo → "Open with Live Server") para ter recarregamento automático enquanto edita.

## O que configurar antes de publicar de verdade

No `index.html`, procure o bloco `CONFIG` no `<script>` final:

```js
const CONFIG = {
  ifood:     "",   // URL da loja no iFood
  whatsapp:  "",   // https://wa.me/55DDNÚMERO
  instagram: "",   // URL do perfil
  utm:       "?utm_source=site&utm_medium=cta"
};
```

Enquanto esses campos estiverem vazios, os botões de pedido mostram um aviso em vez de redirecionar — nada finge estar funcionando.

Para Google Analytics / Meta Pixel, os eventos de clique já disparam para `window.dataLayer` e para `fbq` quando existirem (procure por `function evento(`). Basta colar os scripts oficiais do GA4/Pixel no `<head>`.

## O que editar caso mude preço/custo real

No `precificacao.html`, os valores de insumo, embalagem, mão de obra e taxas de canal (`CANAIS`) são só o ponto de partida — foram estimados a partir de pesquisa de mercado, não medidos na sua cozinha. Assim que você tiver os custos reais de fornecedor, ajuste os campos do formulário (ficam salvos automaticamente ao clicar em "Salvar parâmetros").

## Estrutura de cores e tipografia (para manter consistência se for expandir)

- Fontes: **Bodoni Moda** (display/logotipo) + **Archivo** (texto/UI), via Google Fonts.
- Paleta: `--noite:#1A1210` `--ouro:#C08A2E` `--ouro-claro:#E8C06B` `--creme:#F3EAD8` `--pistacio:#6E8B4E` `--cereja:#9E2F2A`.

Essas variáveis CSS (`:root`) estão duplicadas em cada arquivo porque cada HTML é autocontido — se quiser factorizar em um `styles.css` compartilhado ao editar no Cursor, é só extrair o bloco `:root{...}` de qualquer um dos três arquivos.
