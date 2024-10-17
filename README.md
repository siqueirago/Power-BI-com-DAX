

# Modelagem e Transformação de dados com DAX com Power BI
Curso - NTT DATA - Engenharia de Dados com Python da DIO
## Introdução
Este desafio de projeto envolve a criação de um modelo Star Schema com base em uma tabela unica **Financial Sample**
serão criadas as tebelas **Fato** e **Dimenção**.
Essas novas tabelas serão formadas com uma seleção de colunas específicas que representam diferentes perspectivas do modelo, dessa forma, a partir da tabela 
principal, geraremos as tabelas possíveis para compor o esquema estrela.

Criaremos também a tabela **Calendario** utilizando DAX, com a função CALENDAR, que gera um intervalo de dados, adicionando colunas que especificam
informações sobre o ano, mês, dia, trimestre, etc.,para que possa ser utilizada no esquema estrela.
## Esquema
No formato Star Schema (estrela esquema), as dimensões são ligadas à tabela fato por meio de chaves estrangeiras. Aqui está uma visão geral do relacionamento:
![esquema](https://github.com/user-attachments/assets/9b1706e3-1395-4881-a866-f946d92828cb)
## Criando a Tabela D_calendario
Para criar uma tabela de dimensão de dados no Power BI utilizando DAX , foi utilizado a função CALENDAR, que gera um intervalo de dados.
```dax
D_Calendario = 
ADDCOLUMNS(
    CALENDAR(MIN(F_Vendas[Date]), MAX(F_Vendas[Date])),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMMM"),
    "Quarter", QUARTER([Date]),
    "Day", DAY([Date]),
    "Weekday", WEEKDAY([Date], 2),  -- 2 significa que a semana começa na segunda-feira
    "Weekday Name", FORMAT([Date], "dddd")
)
```
## Explicação do código
* CALENDAR(MIN(F_Vendas[Date]), MAX(F_Vendas[Date]): Esta função cria uma tabela de dados com o intervalo baseado na coluna Date da tabela de vendas (F_Vendas).
* ADDCOLUMNS: Adicionadas novas colunas com informações fornecidas sobre os dados.
* Year: Extrai ou ano da data.
* Month Number: Extrai o número do mês.
* Month Name: Usa FORMAT para retornar o nome completo do mês.
* Quarter: Retorno ao trimestre do ano (1 a 4).
* Day: Retorna o dia do mês.
* Weekday: Retorna o número do dia da semana (1 = Segunda, 7 = Domingo).
* Weekday Name: Retorna o nome completo do dia da semana.

## Link do Projeto
https://app.powerbi.com/links/gWRexM5GFi?ctid=da49a844-e2e3-40af-86a6-c3819d704f49&pbi_source=linkShare&bookmarkGuid=0779b03b-2ab8-4c13-ac07-aa7c288d69e9
