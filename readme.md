# 1. Projeto de Previsão de Séries Temporais com XGBoost

<p align="justify">
Este projeto apresenta uma abordagem de previsão de vendas utilizando modelos de séries temporais baseados em <b>XGBoost</b>. O objetivo principal é simular um ambiente de previsão comercial envolvendo múltiplos clientes e produtos, permitindo analisar como diferentes horizontes temporais influenciam a capacidade preditiva dos modelos.
</p>

<p align="justify">
A proposta utiliza uma estratégia interessante de segmentação temporal: ao invés de treinar um único modelo global para todas as previsões, o projeto cria modelos específicos para cada cliente e para cada horizonte de previsão. Dessa forma, o sistema consegue capturar comportamentos distintos de curto, médio e longo prazo, respeitando particularidades de cada série temporal.
</p>

---

# 2. Objetivo

<p align="justify">
O principal objetivo do projeto é construir um pipeline completo de previsão temporal utilizando dados sintéticos de vendas mensais. O sistema simula um cenário corporativo no qual diferentes clientes possuem padrões próprios de consumo, sazonalidade e crescimento ao longo do tempo.
</p>

<p align="justify">
Além da geração das previsões, o projeto também busca avaliar a qualidade dos modelos por meio de métricas estatísticas e produzir visualizações comparando valores reais e previstos.
</p>

---

# 3. Estrutura dos Dados

<p align="justify">
O dataset foi construído considerando cinco clientes e dez produtos diferentes, distribuídos ao longo de quarenta e oito meses consecutivos. Cada combinação cliente-produto possui um comportamento próprio composto por tendência, sazonalidade e ruído aleatório.
</p>

<p align="justify">
Para tornar o problema mais próximo de um ambiente real, foram inseridos outliers aleatórios nas séries de vendas. Esses pontos representam eventos inesperados, como campanhas promocionais, picos sazonais ou mudanças abruptas no comportamento de compra.
</p>

<p align="justify">
A estrutura temporal do problema permite explorar características importantes de previsão de demanda, principalmente a dependência histórica entre períodos consecutivos.
</p>

---

# 4. Engenharia de Features

<p align="justify">
O projeto utiliza técnicas clássicas de engenharia de atributos para séries temporais. Foram criadas variáveis derivadas do calendário, como mês e ano, além de atributos baseados em atraso temporal, conhecidos como lags.
</p>

<p align="justify">
Os lags permitem que o modelo utilize informações de períodos anteriores para estimar vendas futuras. Também foram utilizadas médias móveis, responsáveis por suavizar oscilações locais e fornecer ao modelo uma visão mais estável do comportamento histórico.
</p>

<p align="justify">
Essa combinação de atributos temporais ajuda o XGBoost a capturar padrões recorrentes, tendências de crescimento e relações não lineares presentes na série.
</p>

---

# 5. Estratégia de Modelagem

<p align="justify">
Um dos pontos mais importantes do projeto é a estratégia de treinamento adotada. Em vez de utilizar apenas um modelo geral, foram treinados quinze modelos independentes.
</p>

<p align="justify">
Cada cliente recebe três modelos diferentes:
</p>

- curto prazo
- médio prazo
- longo prazo

<p align="justify">
Essa abordagem permite especializar os modelos conforme o horizonte temporal desejado. Previsões de curto prazo normalmente dependem fortemente de padrões recentes, enquanto previsões de longo prazo exigem maior capacidade de generalização e identificação de tendências estruturais.
</p>

<p align="justify">
A utilização de modelos específicos reduz o risco de perda de informação causada por comportamentos muito distintos entre clientes e períodos.
</p>

---

# 6. Avaliação dos Modelos

<p align="justify">
A qualidade das previsões foi avaliada utilizando métricas amplamente aplicadas em problemas de regressão.
</p>

<p align="justify">
O MAE mede o erro absoluto médio das previsões, indicando o desvio médio entre valores reais e previstos. O RMSE penaliza erros maiores de forma mais intensa, sendo útil para identificar previsões muito distantes da realidade. Já o coeficiente R² mede a capacidade explicativa do modelo em relação à variabilidade dos dados.
</p>

<p align="justify">
A análise dessas métricas permite verificar como os modelos se comportam em diferentes horizontes temporais e quais clientes apresentam séries mais previsíveis.
</p>

---

# 7. Redistribuição das Previsões por Produto

<p align="justify">
Após prever o volume total de vendas para cada cliente, o projeto redistribui esse valor entre os produtos com base na participação histórica de cada item nas vendas totais.
</p>

<p align="justify">
Essa estratégia é simples, porém bastante eficiente para transformar previsões agregadas em previsões detalhadas por produto. Dessa forma, o sistema consegue produzir estimativas mais próximas de cenários reais de planejamento comercial e controle de estoque.
</p>

---

# 8. Visualização dos Resultados

<p align="justify">
O projeto também apresenta gráficos comparando vendas reais e previstas ao longo do tempo. Essa visualização permite observar a aderência dos modelos ao comportamento histórico da série e identificar períodos em que as previsões apresentam maior desvio.
</p>

<p align="justify">
A comparação visual facilita a interpretação dos resultados e ajuda a entender como o modelo reage a sazonalidades, tendências e outliers presentes nos dados.
</p>

---

# 9. Conclusão

<p align="justify">
O projeto demonstra como técnicas de Machine Learning podem ser aplicadas em problemas de previsão temporal de forma relativamente simples, mas ainda assim eficiente. A utilização de múltiplos modelos especializados por cliente e horizonte temporal permite capturar comportamentos distintos das séries, aumentando a flexibilidade do sistema.
</p>

<p align="justify">
Mesmo utilizando um dataset sintético, a estrutura criada reproduz desafios reais encontrados em ambientes corporativos, como sazonalidade, tendência, ruído e eventos extremos. Além disso, o uso de features temporais clássicas combinado ao XGBoost mostra como modelos baseados em árvores podem alcançar bons resultados em tarefas de forecasting.
</p>

<p align="justify">
A abordagem utilizada também evidencia uma estratégia importante em sistemas preditivos modernos: diferentes horizontes temporais possuem dinâmicas distintas e, por isso, podem se beneficiar de modelos independentes. Essa separação entre curto, médio e longo prazo torna o pipeline mais interpretável, modular e adaptável para aplicações reais de previsão de demanda, planejamento de vendas e gestão de estoque.
</p>

