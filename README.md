# semana15inteligencia


Análise de viabilidade técnica: triagem automatizada
1. Introdução

O objetivo da PoC foi comparar duas formas de fazer uma triagem inicial de pacientes: usando regras em Python e usando um LLM (IA Generativa).

2. Abordagem simbólica: Python

O código Python funciona procurando palavras específicas na frase.

Nos testes:

"Minha cabeça dói um pouco." → retornou ERRO, pois o código procura "dor", mas a frase usa "dói".
"Sinto uma pressão no peito e falta de ar." → retornou ERRO, pois não aparece a palavra "respirar".
"Não consigo puxar o ar e minha visão escureceu." → retornou ERRO.

O teste de falha mostra que o Python não entende o significado das frases. Ele apenas procura palavras que foram programadas previamente.

3. Abordagem generativa: LLM

O LLM consegue analisar o significado da frase, mesmo quando as palavras são diferentes das previstas no código.

No teste:

"Não consigo puxar o ar e minha visão escureceu."

A IA tende a classificar como ALTA, pois entende que "não consigo puxar o ar" indica falta de ar e que "visão escureceu" pode indicar uma situação de desmaio ou pré-desmaio.

No teste de estresse:

"Não estou com febre, na verdade estou gelado e tremendo muito, sentindo uma pontada fina no braço esquerdo."

O Python retorna MÉDIA, porque encontra a palavra "febre", mesmo ela estando negada. Já a IA consegue considerar o contexto e pode classificar como ALTA, devido à combinação dos sintomas.

4. Riscos

Um dos principais riscos do uso de IA é a alucinação, quando o modelo pode inventar informações, diagnósticos ou tratamentos. Também existe o risco de classificar uma situação de forma incorreta.

5. Conclusão

A abordagem Python é simples e previsível, mas possui dificuldade para entender diferentes formas de falar sobre os sintomas.

O LLM consegue compreender melhor o contexto e a linguagem natural, mas também apresenta riscos.

Por isso, a melhor opção seria uma solução híbrida, usando o LLM para interpretar as mensagens e regras de segurança para situações críticas. Em uma aplicação real, o sistema também precisaria ser validado por profissionais de saúde.
