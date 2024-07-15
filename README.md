# 📊 Previsão de Estoque Inteligente na AWS com [SageMaker Canvas](https://aws.amazon.com/pt/sagemaker/canvas/) por Samir Melo

Utilizar Ferramentas de Machine Learning tem sido uma experiencia muito atraente, pois dota essa parte de Análise de Dados chama muito minha atenção 

## 📋 Passos Seguidos no Desafio

1. Realizei um fork para ter acesso aos dados em massa do tipo CSV pelo GitHub da Dio;

2. Depois realizei um git clone do arquivo para minha maquina;

3. com acesso ao Sagemaker Canvas da AWS o arquivo simulando estoque: "dataset-500-curso-sagemaker-canvas-dio" em formato CSV foi inserido como meu Dataset no Sagemaker Canvas;

4. Após definir qual item se desja prever com a análise preditiva, (no meu exemplo a quantidade de estoque), deve-se analisar, algumas sugestões e recomendações feitas pelo próprio Sagemaker Canvas como: 
- Configurações do modelo, suas colunas de identificação e a coluna de referencia temporal. (tudo muito intuitivo e recomendado em sua maior parte pela IA do Sagemaker Canvas).

* Além disso, conhecer seu dataset também é primordial na hora de entender as predições, identificando assim, anomalias, oportunidades e erros no processamento de dados.

- Depois foi escolhido o método de Build, lembrando que quanto mais demorado (ou mais treinado) mais confiáveis serão as análises dos dados para previsão e consequentemente para as tomadas de decisão de seu negócio.


## 🎯 ANÁLISE DE MÉTRICAS ENCONTRADOS

1. Avg. wQL = 0.086 (representa média ponderada de perdas) avaliando a previsão como um todo, se levarmos em consideração que quanto mais próximo de 0 (zero) mais precisão na previsão, nosso modelo está com uma margem boa, apesar do tempo de treino que foi em média 20 min.
2. MAPE = 0.290 (Erro percentual médio absoluto)
vai nos trazer a diferença entre as médias do valor previsto e valor real, levou em consideração os pontos de tempo, neste caso a coluna DIA. se o MAPE for Zero, considera-se um modelo perfeito, livres de erro.
3. WAPE = 0.152 (O erro percentual absoluto ponderado)
Observa o desvio geral entre os valores previsto e observados, tanto o MAPE quanto o WAPES do modelo treinado em questão precisão de maior tempo para treinamento caso queiramos uma melhor previsão, já que o índice ainda estão um pouco longe e zero.
4. RMSE = 1.535 (raiz quadrada dos erros quadráticos médios)
Outro ponto a se melhorar nesse modelo, já que seu índice adicionou o primeiro numero inteiro de todo o modelo treinado (1.535)
5. MASE = 0.180 (Erro médio em escala absoluta)
Média do erro absoluto da previsão normalizada pelo erro médio absoluto de um método simples de previsão de linha de base.
A referencia do MASE para definir um bom modelo treinado é se eles se encontra acima de 1 (um) essa característica indica uma linha de base ruim ou se está abaixo de 1, indicando um modelo estimado com melhor linha de base de dados. Neste caso (0.180) ficando abaixo de 1 (um).

## Conclusão: 
Apesar do MASE ficar abaixo de 1, entender as métricas do modelo utilizado e conhecer o as regras do negocio dos produtos (nesse caso) ou do serviço analisado é fundamental para definir se o modelo atende ou não a demando de seu negócio ou do cliente a depender do caso.
O Modelo treinado não apresentou nenhum tipo de impacto com a coluna promoção na relação com os estoques.** 




## 🤔 PREDICT (PREVISÕES)

### 1. Históricos de demanda:

- Pessimistas (P10)
- Conservadoras (P50)
- Otimistas (P90)

-   Navegue até a pasta `datasets` deste repositório. Esta pasta contém os datasets que você poderá escolher para treinar e testar seu modelo de ML. Sinta-se à vontade para gerar/enriquecer seus próprios datasets, quanto mais você se engajar, mais relevante esse projeto será em seu portfólio.
-   Escolha o dataset que você usará para treinar seu modelo de previsão de estoque.
-   Faça o upload do dataset no SageMaker Canvas.

### Considerações finais

 Utilizando o Type Single Prediction, alguns itens do dataset foram analisados, como item 17 a principio parecia não ter apresentado histórico de demanda pessimista (P10), apenas demandas conservadoras e otimistas, mas após análise detalhada verificou que o P10 e P50 tinha exatamente os mesmo históricos de demandas.

Diferente do item 21 com seu histórico de demanda (10), apresentou P10 = 2.476, P50 = 6.448 e P90 = 12.328 definindo bem a proposta do modelo em analisar previsões de estoques pessimistas, conservadores e otimistas.
