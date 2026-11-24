# Biblioteca gratuita de aulas — Brittech Educação

Aulas gratuitas de exemplo, geradas com o modelo do planejador do MVP
(modo demonstração, sem IA real). Cada aula traz o plano completo e os
slides, em 3 arquivos + o botão de adaptação com IA.

## Estrutura

```
aulas-gratuitas/
├── index.html                  # página da biblioteca (sem dependências externas)
├── educacao-infantil/          # 19 aulas (15 objetivos dos 5 campos + Letramento e Alfabetização, Matemática, Contos Infantis, Libras)
├── fundamental-1/              # 42 aulas (36 habilidades BNCC de 1º a 5º ano + 6 transversais)
├── fundamental-2/              # 41 aulas (35 habilidades BNCC de 6º a 9º ano + 5 transversais + 1 aula da habilidade EF15AR01, do Fundamental 1)
├── ensino-medio/               # 32 aulas (26 habilidades BNCC da 1ª série + 6 transversais)
└── links-gratuitos-verificados.md  # fontes dos 8 links da seção "Livros e plataformas gratuitas"
```

Cada aula tem 3 arquivos com o mesmo nome-base (`<slug>`):

| Arquivo | Conteúdo |
|---|---|
| `<slug>.pptx` | Slides (8) gerados pelo gerador de PPT do MVP — **editável** (texto, notas do apresentador e ilustrações) |
| `<slug>.pdf` | Plano completo + slides com notas, para imprimir |
| `<slug>.docx` | Plano completo em Word — **editável** (texto real, não imagem) |

Além disso, cada aula na página tem o botão **“Adaptar com IA”**, que abre
o planejador com a aula já preenchida (ver abaixo).

## "Adaptar com IA" — como funciona

O botão aponta para o MVP publicado com os dados da aula na URL:

```
https://thiagollipe-web.github.io/brittech-educacao-mvp/?etapa=...&componente=...&ano=...&habilidade=...&tema=...&duracao=50
```

O MVP lê esses parâmetros (`mvp/app.js`, bloco `adaptarComIAViaUrl` no fim
do arquivo) e pré-preenche o formulário. O professor revisa e clica em
“Gerar plano de aula” para a IA escrever uma versão nova.

**Atenção:** o suporte a esses parâmetros existe no `app.js` local. Para o
botão funcionar no site publicado, é preciso republicar o MVP (subir o
`app.js` atualizado para o repositório `brittech-educacao-mvp`).

## Conteúdo

- 134 aulas: 19 Infantil + 42 Fundamental 1 + 41 Fundamental 2 + 32 Médio — uma aula para cada uma das 112 habilidades do catálogo BNCC (64 verificadas, 48 a confirmar), mais as aulas transversais sem código BNCC direto. A habilidade EF15AR01 consta uma única vez no catálogo (Fundamental 1, 1º ao 5º ano), mas é usada em 2 aulas — 1º ano (Fundamental 1) e 6º ano (Fundamental 2) — o que é legítimo: o mesmo código BNCC pode aparecer em mais de uma aula.
- Habilidades do catálogo BNCC (`mvp/bncc.json`). Habilidades marcadas como
  “a confirmar” no catálogo são sinalizadas na página, no plano e no PDF —
  confira no texto oficial da BNCC antes de aplicar. Aulas de componentes
  sem habilidade BNCC direta (Projeto de Vida, Tecnologia e Programação,
  Robótica, Libras, Espanhol no Fundamental, Inglês no Fundamental 1) são
  marcadas como “Sem código BNCC específico — tema transversal”: nenhum
  código foi inventado.
- A página traz ainda a seção “Livros e plataformas gratuitas” com 8 links
  verificados (MEC Livros, MEC Enem, MEC Idiomas, Khan Academy, MakeCode
  micro:bit, Google Colab, Scratch, Domínio Público) — ver
  `links-gratuitos-verificados.md`.
- As aulas são exemplos gratuitos: revise e adapte antes de aplicar.

## Publicar

Subir esta pasta para um repositório no GitHub e ativar o GitHub Pages
(Deploy from a branch, main, / na raiz da pasta) — igual ao MVP. Nada aqui
depende de servidor: são arquivos estáticos.

## Regenerar

Scripts em `~/workspace/plataforma-professores/.trabalho-aulas-v2/`:
`lessons.json` (43 aulas) + `lessons-novos-fund1.json` (6) +
`lessons_novas.json` (5) = 54 aulas; `build_all.py` (PPTs no padrão
aprovado), manifestos de imagens em `imgs/` e o script de atualização da
página em `/tmp/update_index.py`.
