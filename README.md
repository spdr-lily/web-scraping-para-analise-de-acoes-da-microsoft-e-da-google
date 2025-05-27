## **Projeto de Web Scraping e Análise de Ações**

### **1\. Introdução**

Este projeto tem como objetivo utilizar o método de web scraping, desenvolvido para coletar e analisar dados históricos de ações da Microsoft (MSFT) e da Google (GOOG). O projeto utiliza a biblioteca `yfinance` em Python para extrair os dados e as bibliotecas `pandas`, `matplotlib` e `seaborn` para o tratamento e visualização dos dados. O objetivo é comparar o desempenho das ações das duas gigantes da tecnologia ao longo de um período específico.

### **2\. Web Scraping com yfinance**

**Web scraping** é uma técnica para extrair dados de websites. No contexto deste projeto, o web scraping é realizado utilizando a biblioteca `yfinance`, que fornece uma interface para acessar dados do Yahoo Finance.

#### **2.1. Biblioteca yfinance**

A biblioteca yfinance simplifica o processo de obtenção de dados financeiros históricos e em tempo real. Ela permite acessar informações como:

* Preço de abertura, fechamento, máximo e mínimo das ações.  
* Volume de negociação.  
* Dividendos e desdobramentos de ações.

#### **2.2. Extração de Dados**

O código implementa a extração de dados da seguinte forma:

**Instalação da biblioteca:**  
pip install yfinance

**Importação da biblioteca:**  
import yfinance as yf

1. **Definição do ticker:**  
   * O usuário é solicitado a inserir o ticker da ação (e.g., `MSFT` para Microsoft, `GOOG` para Google).  
   * A função `yf.Ticker()` é utilizada para criar um objeto ticker.  
2. **Obtenção do histórico de dados:**

   * O método `ticker.history()` é chamado para obter os dados históricos.  
   * Os parâmetros `period`, `start` e `end` permitem definir o período dos dados. No código, o período é definido como 1 ano.  
     symbol 

\= input("Digite o nome da ação: ")

ticker \= yf.Ticker(symbol)  
historico \= ticker.history(period="1y")

3. **Visualização dos dados (opcional):**

   * A função `print(hist)` exibe os dados brutos extraídos.

### **3\. Visualização dos Dados com Gráficos**

Após a extração, os dados são tratados e visualizados para facilitar a análise.

#### **3.1. Tratamento dos Dados**

1. **Conversão para DataFrame:**

   * Os dados históricos são convertidos em um DataFrame do `pandas` para facilitar a manipulação.

df \= pd.DataFrame(historico\['Close'\])

df.reset\_index(inplace=True)

2. **Preparação para o gráfico:**

   * A coluna 'Date' é mantida como índice para o gráfico.

#### **3.2. Geração dos Gráficos**

O código utiliza as bibliotecas `matplotlib` e `seaborn` para criar um gráfico de linha que representa o preço de fechamento da ação ao longo do tempo.

1. **Configuração do gráfico:**

   * `plt.figure(figsize=(10, 6))` define o tamanho da figura.  
   * `sns.lineplot()` cria o gráfico de linha, onde 'Date' é o eixo x e 'Close' é o eixo y.  
   * `plt.title()`, `plt.xlabel()`, `plt.ylabel()` e `plt.legend()` definem o título, rótulos dos eixos e legenda.  
   * `plt.xticks(rotation=45)` rotaciona os rótulos do eixo x para melhor legibilidade.  
   * `plt.grid(True)` adiciona uma grade ao gráfico.  
   * `plt.show()` exibe o gráfico.

\# Criando gráfico para visualização

plt.figure(figsize=(10, 6))  
sns.lineplot(x='Date', y='Close', data=df, label=symbol)  
plt.title(f'Preço de Fechamento da Ação {symbol}')  
plt.xlabel('Data')  
plt.ylabel('Preço de Fechamento')  
plt.xticks(rotation=45)  
plt.legend()  
plt.grid(True)  
plt.show()

#### **3.3. Gráficos da Microsoft e Google**

Para gerar os gráficos da Microsoft e Google, o código é executado duas vezes, inserindo `MSFT` e `GOOG` como entrada, respectivamente. Isso resulta em dois gráficos distintos, mostrando a evolução dos preços de fechamento de cada ação ao longo do período de 1 ano.

### **4\. Comparação dos Resultados**

A comparação dos resultados é feita visualmente através da análise dos dois gráficos gerados. Foi observada a tendência geral, volatilidade e pontos de inflexão nos preços de fechamento de ambas as ações.

### **5\. Conclusão**

Este projeto demonstra um processo completo de web scraping, tratamento e visualização de dados de ações utilizando Python. A análise comparativa dos gráficos da Microsoft e Google permite obter insights sobre o desempenho relativo das empresas.
