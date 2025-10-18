# 🐾 PetStore Pipeline
[![Live Badge](https://img.shields.io/badge/-Live-2B5482?style=flat-square&logo=streamlit&logoColor=fff)](https://bi-petstore.streamlit.app/)
[![Projeto Badge](https://img.shields.io/badge/-petstore--scraping-2B5482?style=flat-square&logo=github&logoColor=fff)](https://github.com/rafa-trindade/petstore-scraping)
[![Projeto Badge](https://img.shields.io/badge/-petstore--etl-2B5482?style=flat-square&logo=github&logoColor=fff)](https://github.com/rafa-trindade/petstore-etl)
[![Projeto Badge](https://img.shields.io/badge/-petstore--bi-2B5482?style=flat-square&logo=github&logoColor=fff)](https://github.com/rafa-trindade/petstore-bi)


Este repositório serve como **hub do projeto**, documentando o fluxo de dados completo e fornecendo uma visão consolidada do pipeline.

* [`petstore-scraping`](https://github.com/rafa-trindade/petstore-scraping) → coleta de dados (Bronze)
* [`petstore-etl`](https://github.com/rafa-trindade/petstore-etl) → tratamento e enriquecimento (Silver e Gold)
* [`petstore-bi`](https://github.com/rafa-trindade/petstore-bi) → dashboards e análises (BI)

O `petstore-pipeline` demonstra uma **pipeline completa de dados**, do scraping à visualização, mostrando competências em:

* Engenharia de Dados
* ETL e Integração de Dados
* Business Intelligence

---

## 📌 Objetivo:

Demonstrar a **pipeline completa de dados** de franquias do setor pet, desde a coleta bruta até a visualização em dashboards interativos.

---

## 🧩 Fluxo de Dados:

```mermaid
graph TD
    A[petstore-scraping<br>Bronze] --> B[petstore-etl<br>Silver e Gold<br>PostgreSQL]
    B --> C[petstore-bi<br>BI e Dashboards]
```

---

## 📊 Estrutura Geral do Projeto:

| Repositório | Função | Camada | Principais Tecnologias |
| ----------------- | ----------------------------- | ------------------ | -------------------------------------- |
| [`petstore-scraping`](https://github.com/rafa-trindade/petstore-scraping) | Coleta de Dados de Franquias | 🟤 Bronze | Selenium, BeautifulSoup4, lxml, pandas |
| [`petstore-etl`](https://github.com/rafa-trindade/petstore-etl) | Limpeza, Padronização e Carga | ⚪ Silver / 🟡 Gold | requests, SQLAlchemy, pandas, Cep Aberto (API) |
| [`petstore-bi`](https://github.com/rafa-trindade/petstore-bi) | BI e Dashboards | 📊 BI | Streamlit, Plotly, pandas |

---

## 📊 Estrutura dos Dados e Metadados:

Após o processamento dos dados pelo pipeline [`petstore-etl`](https://github.com/rafa-trindade/petstore-etl) e seu carregamento no banco **PostgreSQL**, o projeto **petstore-bi** passa a receber as colunas abaixo, que servirão como base para o enriquecimento progressivo com informações analíticas voltadas ao suporte de decisões estratégicas de expansão.


| Coluna                      | Tipo    | Descrição                         | Valores possíveis / Observações             | Unidade | Camada        | Origem              | Última Atualização |
| --------------------------- | ------- | --------------------------------- | ------------------------------------------- | ------- | ------------- | ------------------- | ------------------ |
| empresa                     | string  | Nome da rede                      | Petz, Cobasi, Petlove...                    | -       | Silver / Gold | petstore-etl        | 2025-10-08         |
| nome                        | string  | Nome da loja                      | -                                           | -       | Silver / Gold | petstore-etl        | 2025-10-08         |
| logradouro                  | string  | Logradouro simplificado           | -                                           | -       | Silver / Gold | petstore-etl        | 2025-10-08         |
| bairro                      | string  | Bairro                            | -                                           | -       | Silver / Gold | petstore-etl        | 2025-10-08         |
| cidade                      | string  | Cidade                            | -                                           | -       | Silver / Gold | petstore-etl        | 2025-10-08         |
| estado                      | string  | Sigla do estado                   | SP, RJ, MG...                               | -       | Silver / Gold | petstore-etl        | 2025-10-08         |
| regiao                      | string  | Região da cidade                  | Norte, Sul, Sudeste, Centro-Oeste, Nordeste | -       | Silver / Gold | IBGE / petstore-etl | 2025-10-08         |
| populacao                   | integer | População estimada da cidade      | Número inteiro                              | pessoas | Silver / Gold | IBGE / petstore-etl | 2025-10-08         |
| cep                         | string  | CEP normalizado                   | 00000-000                                   | -       | Silver / Gold | petstore-etl        | 2025-10-08         |
| latitude                    | float   | Latitude geográfica               | -90 a 90                                    | graus   | Silver / Gold | petstore-etl        | 2025-10-08         |
| longitude                   | float   | Longitude geográfica              | -180 a 180                                  | graus   | Silver / Gold | petstore-etl        | 2025-10-08         |
| renda_domiciliar_per_capita | float   | Renda domiciliar média (estadual) | Valores monetários                          | R$      | Silver / Gold | IBGE / petstore-etl | 2025-10-08         |
| cidade_cod_ibge             | string  | Código IBGE da cidade             | 7 dígitos, conforme IBGE                    | -       | Silver / Gold | IBGE / petstore-etl | 2025-10-08         |
| data_extracao               | date    | Data da extração do dado          | YYYY-MM-DD                                  | -       | Silver / Gold | petstore-etl        | 2025-10-08         |

---

## ⚙️ Tecnologias e Bibliotecas:

O projeto utiliza um conjunto de ferramentas para automação, requisição, tratamento e análise de dados:

* [**pandas**](https://pypi.org/project/pandas/) → manipulação e estruturação de dados tabulares
* [**Selenium**](https://pypi.org/project/selenium/) → automação de navegação e interação com páginas dinâmicas  
* [**BeautifulSoup4**](https://pypi.org/project/beautifulsoup4/) → extração e análise de conteúdo HTML  
* [**lxml**](https://pypi.org/project/lxml/) → parser rápido e eficiente para HTML e XML
* [**requests**](https://pypi.org/project/requests/) → chamadas HTTP para APIs externas  
* [**tabulate**](https://pypi.org/project/tabulate/) → exibição de tabelas no terminal de forma legível  
* [**SQLAlchemy**](https://pypi.org/project/SQLAlchemy/) → conexão e manipulação de bancos de dados SQL de forma programática  
* [**psycopg2-binary**](https://pypi.org/project/psycopg2-binary/) → driver PostgreSQL para Python  
* [**python-dotenv**](https://pypi.org/project/python-dotenv/) → leitura de variáveis de ambiente a partir de arquivos `.env`
* [**plotly**](https://pypi.org/project/plotly/) → visualizações interativas
* [**streamlit**](https://pypi.org/project/streamlit/) → criação de dashboards web

##### O projeto utiliza a API **CEP Aberto** para obter informações de **latitude e longitude**, além de preencher campos ausentes de endereço (logradouro, bairro, cidade, estado, cep).
---

## 🖥️ Log de Execução:

Cada etapa gera logs detalhados de execução:

* **petstore-scraping:** coleta de dados brutos
* **petstore-etl:** transformação e enriquecimento
* **petstore-bi:** eda, tratamento de dados, análise e BI

🔗 [log petstore-scraping](https://raw.githubusercontent.com/rafa-trindade/petstore-scraping/refs/heads/main/logs/log.txt)
🔗 [log petstore-etl](https://raw.githubusercontent.com/rafa-trindade/petstore-etl/refs/heads/main/logs/log.txt)

---

## 🏪 Redes Analisadas:

Atualmente, o projeto coleta dados públicos das seguintes redes para estudo:

* **Cobasi**
* **Pet Camp**
* **Petland**
* **Petlove**
* **Petz**

---

## 📸 Capturas de Tela

#### - Cobasi - Região: Brasil
![Cobasi](https://github.com/rafa-trindade/petstore-bi/blob/main/docs/cobasi-brasil.png)

#### - PetCamp - Região: Sudeste
![PetCamp](https://github.com/rafa-trindade/petstore-bi/blob/main/docs/petcamp-sudeste.png)

#### - Petland - Região: Sul
![Petland](https://github.com/rafa-trindade/petstore-bi/blob/main/docs/petland-sul.png)

#### - Petlove - Estado: SP
![Petlove](https://github.com/rafa-trindade/petstore-bi/blob/main/docs/petlove-sp.png)

#### - Petz - Região: Nordeste
![Petz](https://github.com/rafa-trindade/petstore-bi/blob/main/docs/petz-nordeste.png)

