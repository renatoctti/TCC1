# Lista de Artigos Científicos

1. Steenhoek, B.; Rahman, M. M.; Jiles, R.; Le, W. "An Empirical Study of Deep Learning Models for Vulnerability Detection," ICSE 2023 — 45th IEEE/ACM International Conference on Software Engineering, 2023. DOI: [10.1109/ICSE48619.2023.00188](https://arxiv.org/abs/2212.08109)

2. Charoenwet, W.; Thongtanunam, P.; Pham, V.-T.; Treude, C. "An Empirical Study of Static Analysis Tools for Secure Code Review," ISSTA 2024 — ACM SIGSOFT International Symposium on Software Testing and Analysis, 2024. DOI: [10.1145/3650212.3680313](https://dl.acm.org/doi/10.1145/3650212.3680313)

3. Ding, Y.; Fu, Y.; Ibrahim, O.; Sitawarin, C.; Chen, X.; Alomair, B.; Wagner, D.; Ray, B.; Chen, Y. "Vulnerability Detection with Code Language Models: How Far Are We?," ICSE 2025 — 47th IEEE/ACM International Conference on Software Engineering, 2025. DOI: [10.1109/ICSE55347.2025.00038](https://arxiv.org/abs/2403.18624)

4. Utture, A.; Palsberg, J. "From Leaks to Fixes: Automated Repairs for Resource Leak Warnings," ESEC/FSE 2023 — 31st ACM Joint European Software Engineering Conference and Symposium on the Foundations of Software Engineering, 2023. DOI: [10.1145/3611643.3616267](https://dl.acm.org/doi/10.1145/3611643.3616267)

5. Charoenwet, W.; Thongtanunam, P.; Pham, V.-T.; Treude, C. "Do Developers Use Static Application Security Testing (SAST) Tools Straight Out of the Box? A Large-Scale Empirical Study," ESEM 2024 — 18th ACM/IEEE International Symposium on Empirical Software Engineering and Measurement, 2024. DOI: [10.1145/3674805.3690750](https://dl.acm.org/doi/10.1145/3674805.3690750)

6. Li, K.; Chen, S.; Fan, L.; Feng, R.; Liu, H.; Liu, C.; Liu, Y.; Chen, Y. "A Comprehensive Study on Static Application Security Testing (SAST) Tools for Android," IEEE Transactions on Software Engineering, vol. 50, 2024. DOI: [10.1109/TSE.2024.3488041](https://doi.org/10.1109/TSE.2024.3488041)

7. Nguyen, A. T.; Le, T.-B.; Kochhar, P. S.; Lo, D. "Automated Code-centric Software Vulnerability Assessment: How Far Are We? An Empirical Study in C/C++," ESEM 2024 — 18th ACM/IEEE International Symposium on Empirical Software Engineering and Measurement, 2024. DOI: [10.1145/3674805.3686678](https://arxiv.org/abs/2407.17053)

8. Piantadosi, V.; Scalabrino, S.; Oliveto, R. "On the Effects of Program Slicing for Vulnerability Detection During Code Inspection," Empirical Software Engineering, vol. 30, 2025. DOI: [10.1007/s10664-025-10636-y](https://link.springer.com/article/10.1007/s10664-025-10636-y)

9. Chen, Z.; He, P.; Lyu, M. R. "An Empirical Study on Vulnerability Disclosure Management of Open Source Software Systems," ACM Transactions on Software Engineering and Methodology, 2025. DOI: [10.1145/3716822](https://dl.acm.org/doi/10.1145/3716822)

10. Zhou, C.; Feng, Y.; Su, Z.; Zhang, X. "An Empirical Study of Data Disruption by Ransomware Attacks," ICSE 2024 — 46th IEEE/ACM International Conference on Software Engineering, 2024. DOI: [10.1145/3597503.3639090](https://dl.acm.org/doi/10.1145/3597503.3639090)

---

# Tema do TCC

**"Avaliação comparativa de ferramentas SAST e modelos de linguagem na detecção de vulnerabilidades reais em projetos open source"**

---

# Trabalhos Similares Existentes

| # | Paper | Ano | O que fez | Limitação |
|---|-------|-----|-----------|-----------|
| 1 | Zhou et al. — "Comparison of SAST Tools and LLMs for Repo-level Vulnerability Detection" | 2024 | Comparou 15 SAST + 12 LLMs em CVEs reais (Java, C, Python) | Só LLMs open-source pequenos (até 8B). Sem GPT-4/Claude |
| 2 | Gnieciak & Szandala — "LLMs vs Static Code Analysis Tools: A Systematic Benchmark" | 2025 | SonarQube, CodeQL, Snyk vs GPT-4.1, Mistral, DeepSeek | Só C#, dataset sintético (63 vulns embutidas, não CVEs reais) |
| 3 | IRIS — Li et al. — "LLM-Assisted Static Analysis for Detecting Security Vulnerabilities" | 2025 | Pipeline híbrido CodeQL + GPT-4 em Java | Só Java, só CodeQL, só GPT-4 |
| 4 | CASTLE — Dubniczky et al. — "Benchmarking Dataset for Static Code Analyzers and LLMs towards CWE Detection" | 2025 | 13 SAST + 10 LLMs em micro-benchmarks | Snippets sintéticos, não código real |
| 5 | Ding et al. (PrimeVul) — "Vulnerability Detection with Code Language Models: How Far Are We?" | 2025 | Benchmark rigoroso mostra LLMs performam perto de aleatório | Não compara com SAST |
| 6 | ZeroFalse — "Improving Precision in Static Analysis with LLMs" | 2025 | LLM filtra falsos positivos de SAST | Só OWASP Benchmark Java |
| 7 | Khare et al. — "Understanding the Effectiveness of LLMs in Detecting Security Vulnerabilities" | 2024 | 16 LLMs em 5.000 amostras de 5 datasets | Não compara com SAST diretamente |

---

# Opções de Diferencial

## Opção A: Comparação Direta — LLMs Frontier vs SAST em CVEs Reais

**Pergunta central:** "Quem detecta mais vulnerabilidades reais em projetos open source: ferramentas SAST tradicionais ou LLMs de última geração?"

### Por que é diferencial
- Zhou (2024) fez algo similar mas só com LLMs pequenos open-source (CodeBERT 0.13B, StarCoder 7B, etc.)
- Gnieciak (2025) usou GPT-4 mas em C# com vulnerabilidades artificiais
- **Ninguém testou GPT-4 + Claude + Gemini em CVEs reais de múltiplos projetos e linguagens**

### Metodologia

**Fase 1 — Construção do Dataset (Semanas 1-3)**
1. Selecionar 100-200 CVEs reais do banco NVD (National Vulnerability Database)
2. Filtrar por: projetos open source no GitHub, com commit de fix identificado
3. Linguagens: Java + Python (ou C/C++) — pelo menos 2
4. Para cada CVE: extrair o commit vulnerável (antes do fix) e o commit corrigido
5. Alternativa: usar dataset pronto — **CVEfixes** (12.107 commits) ou **PrimeVul** (6.968 funções vulneráveis)

**Fase 2 — Execução das Ferramentas SAST (Semanas 3-5)**
1. Instalar e configurar:
   - **CodeQL** (GitHub, gratuito) — considerada a mais poderosa
   - **Semgrep** (open source) — rápida, baseada em padrões
   - **SonarQube** (Community Edition, gratuito) — a mais usada na indústria
2. Para cada projeto/CVE: rodar as 3 ferramentas no commit vulnerável
3. Registrar: detectou a vulnerabilidade? Quantos alertas no total? Falsos positivos?

**Fase 3 — Execução dos LLMs (Semanas 5-8)**
1. Para cada função/arquivo vulnerável, enviar para:
   - **GPT-4** (via API OpenAI)
   - **Claude Sonnet/Opus** (via API Anthropic)
   - **Gemini Pro** (via API Google) — opcional
   - **DeepSeek Coder** ou **CodeLlama** (local, gratuito) — para comparação
2. Prompt padronizado: "Analise o seguinte código e identifique vulnerabilidades de segurança. Para cada uma, indique o tipo (CWE), a linha e a severidade."
3. Testar 2-3 estratégias de prompt: zero-shot, few-shot, chain-of-thought
4. Registrar: detectou? Classificou corretamente o CWE? Falsos positivos?

**Fase 4 — Análise Comparativa (Semanas 8-10)**
1. Métricas: Precision, Recall, F1-Score, taxa de falsos positivos
2. Comparar: SAST individual vs LLM individual vs combinação de SAST vs combinação de LLMs
3. Analisar por tipo de vulnerabilidade (CWE): quem é melhor em quê?
4. Analisar por linguagem: diferença entre Java e Python?
5. Custo: tempo de execução de cada ferramenta + custo de tokens API

**Fase 5 — Escrita (Semanas 10-16)**

### Resultados esperados
- Tabela comparativa completa SAST vs LLMs
- Análise de quais tipos de vulnerabilidade cada abordagem detecta melhor
- Recomendações práticas para desenvolvedores

| Critério | Valor |
|----------|-------|
| Dificuldade | Média |
| Tempo | 14-16 semanas |
| Custo API | $50-200 |
| Inovação | Boa |
| Rigor científico | Bom |
| Risco de não terminar | Baixo |

---

## Opção B: Pipeline Híbrido — SAST Detecta, LLM Filtra

**Pergunta central:** "É possível usar LLMs para reduzir os falsos positivos de ferramentas SAST, criando um pipeline mais eficiente?"

### Por que é diferencial
- IRIS (2025) fez algo parecido mas SÓ com CodeQL + GPT-4 em Java
- ZeroFalse (2025) usou OWASP Benchmark (sintético)
- **Ninguém generalizou para múltiplas SAST tools + múltiplos LLMs em CVEs reais**
- Problema real da indústria: SAST gera tantos alertas que desenvolvedores ignoram (alert fatigue)

### Metodologia

**Fase 1 — Construção do Dataset (Semanas 1-3)**
- Mesmo que Opção A: 100-200 CVEs reais, projetos open source

**Fase 2 — Execução das Ferramentas SAST (Semanas 3-5)**
1. Rodar CodeQL, Semgrep, SonarQube em cada projeto
2. Coletar TODOS os alertas (não só os relacionados ao CVE)
3. Classificar manualmente cada alerta como: Verdadeiro Positivo (VP) ou Falso Positivo (FP)
4. Essa é a parte mais trabalhosa — precisa de validação manual

**Fase 3 — Pipeline Híbrido (Semanas 5-9)**
1. Para cada alerta SAST, montar um prompt com:
   - O trecho de código apontado pelo alerta
   - A mensagem de alerta da ferramenta SAST
   - O contexto ao redor (função completa ou arquivo)
2. Enviar para GPT-4 / Claude: "A ferramenta X gerou o seguinte alerta de segurança para este código. Analise se este alerta é um verdadeiro positivo ou falso positivo. Justifique."
3. Registrar a decisão do LLM para cada alerta

**Fase 4 — Avaliação do Pipeline (Semanas 9-12)**
1. Comparar as decisões do LLM com a classificação manual (ground truth)
2. Métricas: quantos FPs filtrados, quantos VPs descartados erroneamente, Precision e Recall do filtro
3. Comparar: SAST sozinha vs SAST + filtro LLM
4. Analisar por ferramenta SAST e por tipo de vulnerabilidade

**Fase 5 — Escrita (Semanas 12-18)**

### Resultados esperados
- Pipeline funcional que reduz falsos positivos
- Evidência de que LLMs podem complementar SAST (não substituir)
- Análise de quais combinações SAST+LLM funcionam melhor

| Critério | Valor |
|----------|-------|
| Dificuldade | Alta |
| Tempo | 16-18 semanas |
| Custo API | $100-300 |
| Inovação | Muito boa |
| Rigor científico | Bom |
| Risco de não terminar | Médio |

---

## Opção C: Análise Temporal — LLMs Sabem ou Decoraram?

**Pergunta central:** "Os LLMs realmente entendem vulnerabilidades de segurança, ou apenas memorizam CVEs que viram no treinamento?"

### Por que é diferencial
- Ding et al. (ICSE 2025) mostrou que LLMs performam mal com critérios rigorosos — mas não separou CVEs pré/pós-cutoff
- LiveCVEBench tenta resolver isso mas é limitado e não compara com SAST
- **Ninguém fez uma análise temporal sistemática comparando SAST vs LLM com controle de contaminação**
- Questão fundamental: se o LLM "decorou" o Log4Shell, isso não é detecção real

### Metodologia

**Fase 1 — Construção do Dataset Temporal (Semanas 1-4)**
1. Levantar as datas de cutoff de treinamento de cada LLM:
   - GPT-4: abril 2024
   - Claude 3.5 Sonnet: abril 2024
   - GPT-4o: outubro 2023
   - (verificar datas exatas na documentação)
2. Dividir CVEs em dois grupos:
   - **Grupo PRÉ-cutoff:** CVEs publicadas ANTES do cutoff (LLM pode ter visto)
   - **Grupo PÓS-cutoff:** CVEs publicadas DEPOIS do cutoff (LLM nunca viu)
3. Selecionar ~100 CVEs de cada grupo, balanceadas por tipo (CWE) e linguagem
4. Fonte: NVD com filtro por data de publicação

**Fase 2 — Execução (Semanas 4-8)**
1. Rodar SAST tools nos dois grupos (SAST não tem problema de contaminação)
2. Rodar LLMs nos dois grupos com o mesmo prompt
3. Registrar resultados separadamente para cada grupo

**Fase 3 — Análise Temporal (Semanas 8-11)**
1. Comparar performance dos LLMs no grupo PRÉ vs PÓS:
   - Se performance é similar → LLM realmente entende segurança
   - Se performance cai drasticamente no PÓS → LLM estava "decorando"
2. Comparar com SAST (que não deveria ter diferença entre grupos)
3. Calcular "taxa de contaminação" = diferença de performance entre grupos
4. Analisar por tipo de CWE: quais vulnerabilidades o LLM "decora" mais?

**Fase 4 — Comparação com SAST (Semanas 11-13)**
1. No grupo PÓS-cutoff (onde não há contaminação):
   - SAST vs LLM: quem é melhor "de verdade"?
2. Essa comparação é a mais justa possível

**Fase 5 — Escrita (Semanas 13-18)**

### Resultados esperados
- Evidência quantitativa de contaminação (ou não) nos LLMs
- Comparação justa SAST vs LLM (sem efeito de memorização)
- Contribuição para o debate "LLMs realmente entendem código?"

| Critério | Valor |
|----------|-------|
| Dificuldade | Média-Alta |
| Tempo | 16-18 semanas |
| Custo API | $50-200 |
| Inovação | Muito boa |
| Rigor científico | Excelente |
| Risco de não terminar | Baixo-Médio |

---

# Comparação Final das Opções

| Critério | Opção A (SAST vs LLM) | Opção B (Híbrido) | Opção C (Temporal) |
|----------|----------------------|--------------------|--------------------|
| Dificuldade | Média | Alta | Média-Alta |
| Tempo estimado | 14-16 semanas | 16-18 semanas | 16-18 semanas |
| Custo API | $50-200 | $100-300 | $50-200 |
| Inovação | Boa | Muito boa | Muito boa |
| Rigor científico | Bom | Bom | Excelente |
| Risco de não terminar | Baixo | Médio | Baixo-Médio |
| Facilidade de apresentar | Alta | Média | Média |
| Utilidade prática | Alta | Muito alta | Média |
| Chance de publicação | Boa | Muito boa | Muito boa |

**Recomendação:** Opção A como base + elementos da Opção C (divisão temporal como seção adicional da análise)
