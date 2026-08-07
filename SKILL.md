# Skill: ventura.interview — LOOP Skill Engine / Deterministic Replay

![Apache-2.0](https://img.shields.io/github/license/chamseddinehiddoud/ventura.interview)
![stars](https://img.shields.io/github/stars/chamseddinehiddoud/ventura.interview)
![forks](https://img.shields.io/github/forks/chamseddinehiddoud/ventura.interview)

Skill de preparação para entrevistas técnicas com **execução determinística**:
explore a vaga uma vez, compile o plano, replique o treino diário com ~zero
tokens, regenere quando o processo (ou a meta) mudar.

## Trigger

Use quando o usuário quiser: preparar entrevista técnica, treinar algoritmos,
revisar fundamentos, praticar system design, montar plano de estudos para
processo seletivo, simular entrevista.

## Arquitetura Token-Efficient & Regenerative

| Fase | Descrição | Consumo |
|---|---|---|
| **Explore** | Modelo forte analisa vaga/empresa/nível (uma vez) | Alto (único) |
| **Compile** | Gera `plano.md`: trilhas, semanas, metas, checklist | Baixo |
| **Replay** | Treino do dia — problema, padrão, tempo, revisão | Mínimo/Zero |
| **Regenerate** | Vaga/trilha mudou → regenere o plano | Sob demanda |

## Receita determinística (Replay)

```text
1. PEDIDO   — "treino de hoje" | "problema do dia" | "simulado"
2. RECEITA  — consulta plano.md: dia N, trilha, problema, padrão, meta
3. EXECUTA  — 1. resolve com tempo limite | 2. valida | 3. revisa solução ótima
4. REGISTRA — dificuldade, padrão usado, tempo, lição
5. STOP-YIELD — estagnação em padrão/trilha → propõe troca de foco
```

## Regras de engenharia

- **Token Budget** — Explore: até 6k tokens. Replay: < 200 tokens.
- **Context Firewall** — o replay só vê o treino do dia (nunca o plano inteiro).
- **Prefix Caching** — o sistema deste arquivo fica byte-stable.
- **Skill Distillation** — treino validado vira plano permanente.
- **Regeneração** — nova vaga/empresa → volta ao Explore com memória.

## Como compilar o plano (Explore → Compile)

```text
1. Entrevista rápida: vaga, empresa, prazo, nível, pontos fracos
2. Seleciona trilhas (fundamentos/algoritmos/sistemas/comportamental)
3. Compila plano.md: 4 semanas, dias, problemas, metas, simulados
4. Valida com o usuário e ativa o Replay
```

## Exemplo de uso

```text
Atue como ventura.interview (modo REPLAY). Meu plano.md diz: "Semana 3, Dia 2:
system design — cache e filas". Liste o tópico, o exercício e a meta de tempo
para hoje. Use menos de 200 tokens e registre o progresso.
```
