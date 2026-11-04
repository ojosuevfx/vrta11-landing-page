# VRTA11 · Página Always On

Landing page do VRTA11 (FII de papel da Fator Verità), construída em um único arquivo HTML, sem framework e sem build.

## Estrutura

```
index.html              página completa (HTML, CSS e JS inline)
assets/
  hero-construction.mp4 vídeo do hero, re-encodado com keyframe em todo frame (scrub pelo scroll)
  hero-poster.jpg       primeiro frame, usado como poster
  tradicao.jpg          imagem da seção "Um dos mais antigos e tradicionais do mercado"
docs/
  pantanal-geradores-landing-page.mdx  engenharia reversa da referência visual usada como base
tools/
  serve.js              servidor estático local com suporte a HTTP Range (necessário para o vídeo)
```

## Rodar localmente

O vídeo do hero é buscado por `currentTime`, o que exige um servidor com suporte a requisições Range. O `http.server` do Python não serve. Use o script incluído:

```bash
node tools/serve.js 8787
```

Depois abra `http://localhost:8787/index.html`.

Em produção qualquer servidor ou CDN comum (Nginx, Apache, Vercel, Netlify, S3, GitHub Pages) já suporta Range. Além disso a página baixa o vídeo inteiro como Blob antes de iniciar, então o seek funciona mesmo sem Range.

## Dependências externas

- Google Fonts: Montserrat
- Lenis 1.3.27 (scroll suave), via jsDelivr

Tudo o mais (botões animados, calculadora, carteira interativa, hero controlado pelo scroll) é CSS e JS puro dentro do `index.html`.

## Pendências de conteúdo

- Todos os botões "Clique aqui para ter mais informações" e "Conheça o VRTA11" apontam para `#` (`data-link="a definir"`).
- As etiquetas amarelas **NOTA** marcam dados a confirmar no último relatório gerencial.
- Os gráficos de evolução patrimonial e de performance 12 meses estão como placeholder.
- O docx de origem traz dois números divergentes para o desconto da cota (14,5% e 12%) e para cotistas (+95 mil e +100 mil); a página mantém os dois como no documento.

## Marca

Cores da Fator: âmbar `#FAAF00`, escuro `#0F1218`, cinzas quentes. Logo oficial em SVG inline (versão marrom na navbar e branca no rodapé).
