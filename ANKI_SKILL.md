---
name: anki-cards-deep-learning
description: Transforma resumos, anotações, transcrições de aula ou trechos de livro sobre Deep Learning, Machine Learning, Estatística, Matemática e áreas afins em cartões Anki atômicos, desenhados para retenção de longo prazo com repetição espaçada. Use sempre que o usuário colar material de estudo e pedir cartões, flashcards, Anki, "revisão", "memorizar", "fixar" ou "formato Anki / CSV para Anki", mesmo que não use a palavra "cartão". Também use para revisar, melhorar ou dividir cartões Anki já existentes.
---

# Gerador de Cartões Anki (retenção de longo prazo)

## Objetivo

Converter material de estudo em cartões que o estudante ainda consiga responder **meses depois**, com revisões rápidas e poucas falhas por ambiguidade.

O cartão não é um resumo em formato de pergunta. É um **gatilho de recuperação**: a pergunta deve levar o cérebro a reconstruir uma ideia específica, sem pistas desnecessárias e sem margem para duas respostas corretas.

Princípio central: **menos cartões, mais precisos, mais independentes.**

---

## Fluxo de trabalho

Siga nesta ordem. Não mostre as etapas 1 a 3 ao usuário; apenas o resultado final.

1. **Mapear o material.** Identifique conceitos, relações, fórmulas, hipóteses, contrastes e armadilhas comuns. Não assuma que o texto está bem organizado: reconstrua a lógica necessária.
2. **Filtrar.** Para cada candidato, pergunte: *"Vale a pena lembrar disso daqui a um ano?"* Descarte trivialidades, exemplos ilustrativos sem valor conceitual, detalhes que se resolvem com uma busca rápida e informação puramente contextual da aula.
3. **Checar compreensão.** Se um ponto importante está confuso, contraditório ou superficial no resumo, **não crie cartão sobre ele**. Sinalize em Observações (ver "Marcadores"). Memorizar o que não se entende gera lembrança frágil.
4. **Redigir cartões** seguindo as regras abaixo.
5. **Revisar** com a checklist de qualidade e remover o que falhar.
6. **Entregar** no formato pedido.

Se o usuário não especificou nada além do material, **não faça perguntas antes**: gere os cartões e explicite suposições nas Observações. Se ele já tiver enviado cartões anteriores, evite duplicá-los.

---

## Regras de criação

### 1. Um cartão = uma ideia atômica

A resposta deve ser **1 a 2 frases** (máximo 3). Se precisar de mais, divida.

Ruim: *Explique como funciona o backpropagation.*

Melhor, em cartões separados:
- Qual é o objetivo do backpropagation?
- Qual regra do cálculo permite propagar o gradiente camada a camada?
- Por que o backpropagation é mais eficiente do que calcular cada derivada parcial isoladamente?

### 2. A pergunta deve ser autossuficiente

O estudante vai ver o cartão sem o resumo e sem lembrar de qual aula veio.

- Nunca escreva "no texto", "segundo o resumo", "como visto antes".
- Inclua o **contexto mínimo** quando o termo for ambíguo: *"Em redes neurais, ..."*, *"Na regressão logística, ..."*, *"No Adam, ..."*.
- Evite perguntas vagas: "Fale sobre", "Explique", "O que é X?" quando X tem vários sentidos. Use verbos específicos: *definir, distinguir, justificar, prever, calcular, identificar*.

### 3. Recuperação ativa, nunca reconhecimento

O estudante deve **produzir** a resposta.

- Evite perguntas de sim/não. Reformule para "por quê", "como", "o que acontece se".
- Evite perguntas cuja resposta está embutida no enunciado.
- Evite enumerações longas ("liste os 6 tipos de..."). Veja a regra 8.

### 4. Priorize o porquê e o mecanismo

Sempre que possível, transforme fatos em: *por quê? como? qual a consequência? qual a diferença? em que situação? o que acontece se...?*

Uma resposta de "por quê" deve conter o **mecanismo causal**, não apenas repetir a pergunta.

Ruim: *Por que usar ReLU? → Porque ela funciona melhor.*
Bom: *Por que ReLU atenua o vanishing gradient em redes profundas? → Porque sua derivada é 1 para entradas positivas, então o gradiente não é encolhido a cada camada, ao contrário da sigmoid, cuja derivada é no máximo 0,25.*

### 5. Preserve a intuição

Para conceitos centrais, crie ao menos um cartão que teste a explicação intuitiva ("o que isso significa na prática?"), além do cartão formal.

### 6. Fórmulas

- Escreva a fórmula corretamente e defina as variáveis **na resposta**, de forma compacta.
- Crie um segundo cartão de **interpretação** só quando agregar compreensão (por exemplo, "o que acontece com a perda quando a probabilidade da classe correta tende a 0?").
- Não crie um cartão para cada símbolo.
- Para fórmulas longas, prefira cartões do tipo "qual termo da fórmula faz X?" (cloze sobre o termo) em vez de exigir reescrever tudo de memória.
- Prefira testar **quando e por que** usar a fórmula, e não apenas sua grafia.

### 7. Comparações e interferência

Conceitos parecidos (L1 vs L2, BatchNorm vs LayerNorm, precisão vs recall) geram confusão entre cartões.

- Crie **um cartão comparativo** com o eixo de diferença bem definido.
- Em cartões individuais desses conceitos, inclua um **elemento distintivo** na pergunta, para que não pareçam o mesmo cartão.
- Se dois cartões têm perguntas quase idênticas e respostas diferentes, reescreva um deles.

### 8. Listas e conjuntos

Listas são a principal causa de cartões que "nunca fixam".

- Se os itens são independentes, **um cartão por item**, com contexto.
- Se a ordem ou a completude importam, use **cloze sobrepostos** (um item oculto por vez, o restante visível).
- Se a lista tem mais de 4 itens e não é essencial decorá-la inteira, mantenha só os itens conceitualmente importantes.

### 9. Cloze: use com critério

Use cloze quando a **frase completa** carrega o sentido e ocultar um termo-chave torna o cartão mais eficiente.

- No máximo 2 lacunas por cartão, e cada uma deve ser um conceito relevante, não uma palavra de ligação.
- A frase precisa ter pistas suficientes para uma única resposta possível.
- Não use cloze por variedade, nem para definições longas.

### 10. Cartões reversos

Crie o sentido inverso (definição → termo) **apenas** quando o estudante precisa evocar o nome do conceito sozinho (jargão, nomes de teoremas, nomes de técnicas). Para o resto, um sentido basta.

### 11. Fidelidade ao material

- Use prioritariamente o material fornecido.
- Corrija pequenos erros evidentes e **avise** (marcador `[CORREÇÃO]`).
- Não acrescente conteúdo avançado não relacionado ao resumo.
- Não invente respostas para lacunas: use `[INFORMAÇÃO INCOMPLETA]` e não gere o cartão.

### 12. Sem redundância

Consolide cartões que testam a mesma coisa em um único mais forte. Exceção: o mesmo conceito testado de **ângulos genuinamente diferentes** (definição, intuição, consequência) é desejável e não conta como redundância.

---

## Tipos de cartão

| Tipo | Quando usar |
| ---- | ----------- |
| BASIC | Pergunta direta com resposta curta e objetiva |
| WHY | Causalidade e mecanismo ("Por que...?") |
| COMPARE | Diferença entre conceitos parecidos, com eixo explícito |
| FORMULA | Fórmula + significado das variáveis |
| APPLICATION | Cenário hipotético que exige aplicar o conceito |
| CLOZE | Frase em que ocultar um termo-chave é mais eficiente |

---

## Distribuição (guia, não regra rígida)

Como ponto de partida: ~30% fundamentos, ~40% entendimento (relações, intuição, causalidade), ~20% aplicação/comparação, ~10% matemática. Ajuste conforme o conteúdo: um resumo muito matemático pode inverter isso. **A qualidade vale mais que a proporção.**

Calibre o volume: em geral, **3 a 8 cartões por página de resumo denso**. Se estiver gerando muito mais, provavelmente está resumindo em vez de selecionando.

---

## Checklist de qualidade

Antes de incluir cada cartão, confirme (mentalmente):

1. Alguém que estudou o tema há um mês consegue responder **apenas lendo a pergunta**?
2. Existe **uma única resposta correta** e objetiva?
3. A resposta cabe em 1 a 3 frases e se revisa em menos de ~15 segundos?
4. A pergunta exige **produzir**, não reconhecer?
5. A pergunta não entrega a resposta nem usa pistas superficiais?
6. É diferente de outros cartões o bastante para não gerar interferência?
7. A informação está **correta** e suficientemente precisa?
8. Vale a pena lembrar disso daqui a um ano?

Falhou em qualquer item: reescreva ou remova.

---

## Marcadores especiais

- `[INFORMAÇÃO INCOMPLETA]`: o resumo é ambíguo ou omite algo necessário. Não gere o cartão; descreva o que falta nas Observações.
- `[CORREÇÃO]`: o resumo continha um erro evidente que foi corrigido no cartão. Diga qual.
- `[PRÉ-REQUISITO]`: o conteúdo depende de um conceito que o resumo não cobre. Sugira estudá-lo antes, sem criar cartão sobre ele.

---

## Formato de saída

Tabela com estas colunas:

| # | Tipo | Pergunta | Resposta | Extra | Tags |
| - | ---- | -------- | -------- | ----- | ---- |

- **Extra** é opcional: um exemplo curto, uma observação ou o "porquê" que reforça a resposta sem inflar o cartão. Deixe vazio quando não agregar.
- **Matemática na tabela:** use `$...$` (inline) e `$$...$$` (bloco) para legibilidade.
- **Idioma:** português, mantendo termos técnicos consagrados em inglês (learning rate, backpropagation, overfitting).

### Tags

Use no máximo 3 tags por cartão, de um vocabulário estável, em formato hierárquico:

`DL::Optimization`, `DL::NeuralNetworks`, `DL::CNN`, `DL::Transformers`, `ML::Regularization`, `Math::LinearAlgebra`, `Math::Calculus`, `Stats::Probability`, `Stats::Inference`

Adicione uma tag de fonte quando o usuário indicar (por exemplo, `Fonte::CursoX`, `Fonte::Goodfellow`). Reutilize tags existentes em vez de criar variações.

### Fechamento

Depois da tabela, apresente apenas:

**Total de cartões:** X

**Observações:** somente se houver erros, ambiguidades, suposições, informações incompletas ou pré-requisitos relevantes.

Não adicione explicações longas fora da tabela.

---

## Exportação para Anki

Quando o usuário pedir "formato Anki", "CSV para Anki" ou equivalente, gere o conteúdo em bloco de código, **sem numeração**, pronto para colar em um arquivo `.txt` e importar.

### Convenções obrigatórias

- Separador: **TAB**. Uma linha por nota.
- HTML ativado. Use `<br>` para quebras de linha, `<b>` para negrito, `<ul><li>` para listas.
- **Matemática no padrão do Anki/MathJax:** inline `\( ... \)` e bloco `\[ ... \]`. **Não use `$...$` nem `$$...$$`**, que o Anki não renderiza por padrão. Converta qualquer fórmula da tabela.
- Aspas e tabulações dentro do texto: evite TABs no conteúdo. Se houver aspas duplas, prefira `&quot;` ou reescreva a frase.
- Tags separadas por **espaço**, sem espaços internos (use `::` para hierarquia).

### Cartões BASIC / WHY / COMPARE / FORMULA / APPLICATION

Cabeçalho do arquivo:

```
#separator:tab
#html:true
#notetype:Basic
#deck:DL
#tags column:4
```

Cada linha:

`Pergunta<TAB>Resposta<TAB>Extra<TAB>Tags`

Se o tipo de nota "Basic" do usuário só tiver dois campos, junte Extra à Resposta (`<br><i>Extra</i>`) e ajuste `#tags column` para 3.

### Cartões CLOZE (arquivo separado)

Cloze usa outro tipo de nota, então **gere em bloco separado**:

```
#separator:tab
#html:true
#notetype:Cloze
#deck:DL
#tags column:3
```

Cada linha:

`Texto com {{c1::lacuna}}<TAB>Extra<TAB>Tags`

Avise em uma linha que os dois blocos devem ser importados separadamente.

---

## Anti-padrões (nunca faça)

- Perguntas do tipo "Explique tudo sobre X" ou "Fale sobre X".
- Respostas com parágrafos, listas longas ou "mini-capítulos".
- Perguntas que só funcionam com o resumo ao lado.
- Cartões de sim/não.
- Cloze com lacunas em palavras triviais ou com várias lacunas independentes.
- Cartões para cada símbolo de uma fórmula.
- Dois cartões quase idênticos com respostas diferentes.
- Gerar cartão sobre algo que o próprio resumo deixa confuso.
- Inflar o volume para "cobrir tudo".