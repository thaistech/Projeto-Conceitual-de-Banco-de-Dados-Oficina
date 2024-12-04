# Projeto-Conceitual-de-Banco-de-Dados-Oficina

## 🔑 Entidades Principais

O diagrama de relacionamento abrange as seguintes entidades:

- **Cliente:** Representa os clientes da oficina mecânica.

- **Veículo:** Representa os veículos dos clientes que são levados à oficina.

- **Mecânicos:** Representa os mecânicos que trabalham na oficina.

- **Equipes:** Representa as equipes de mecânicos responsáveis pela execução dos serviços nas ordens de serviço.

- **Ordem de Serviços (OS):** Representa as ordens de serviço abertas para consertar ou fazer a revisão dos veículos.

- **Serviços:** Representa os serviços que podem ser realizados na oficina, como trocas de óleo, alinhamento, entre outros.

- **Peças:** Representa as peças usadas para realizar os serviços nas ordens de serviço. <br><br>

## 🔄 Relacionamentos no Banco de Dados

O modelo de dados define vários relacionamentos, incluindo: <br>

**Relacionamentos N:M (Muitos para Muitos):**

- **Ordens de Serviço (OS) → Serviços:** Uma OS pode ter vários serviços, e um serviço pode ser parte de várias OS. Esse relacionamento é intermediado pela tabela ordem_servico_servicos.

- **Ordens de Serviço (OS) → Peças:** Uma OS pode ter várias peças, e uma peça pode ser parte de várias OS. Esse relacionamento é intermediado pela tabela ordem_servico_pecas.

- **Mecânicos → Equipes:** Um mecânico pode fazer parte de várias equipes, e uma equipe pode ter vários mecânicos. <br>

**Relacionamentos 1:N (Um para Muitos):**

- **Clientes → Veículos:** Um cliente pode ter vários veículos.

- **Ordens de Serviço (OS):** Uma OS é associada a uma equipe que é responsável pela execução dos serviços.

- **Veículos → Ordens de Serviço (OS):** Um veículo pode ter várias ordens de serviço associadas.<br><br>

## 📊 Estrutura do Banco de Dados

Cada tabela no banco de dados foi projetada para representar uma entidade, com os seguintes detalhes:

- **Chaves Primárias (PK)** e **Chaves Estrangeiras (FK)** foram implementadas para garantir a integridade referencial.
- **Tabelas de junção** foram criadas para gerenciar relacionamentos muitos-para-muitos, como ordem_servico_servicos e ordem_servico_pecas.

**Tabelas Criadas:**
1. Clientes:
- Representa os clientes da oficina mecânica.
- Atributos: id_cliente (PK), nome, endereco, telefone, email.
- Relacionamentos: Cada cliente pode ter vários veículos (1:N com a tabela veiculos).

2. Veículos:
- Representa os veículos dos clientes que são levados à oficina.
- Atributos: id_veiculo (PK), placa, modelo, marca, ano, id_cliente (FK).
- Relacionamentos: Cada veículo pode ter várias ordens de serviço associadas (1:N com a tabela ordens_servico).

3. Mecânicos:
- Representa os mecânicos que trabalham na oficina.
- Atributos: id_mecanico (PK), nome, endereco, especialidade.
- Relacionamentos: Um mecânico pode fazer parte de várias equipes (N:M com a tabela equipes).

4. Equipes:
- Representa as equipes de mecânicos responsáveis pela execução dos serviços nas ordens de serviço.
- Atributos: id_equipe (PK), nome.
- Relacionamentos: Uma equipe pode ser associada a várias ordens de serviço (1:N com a tabela ordens_servico).

5. Ordens de Serviço (OS):
- Representa as ordens de serviço abertas para consertar ou revisar os veículos.
- Atributos: id_os (PK), numero_os, data_emissao, valor_total, status, data_conclusao, id_cliente (FK), id_veiculo (FK), id_equipe (FK).
- Relacionamentos: Uma ordem de serviço pode conter vários serviços e várias peças (N:M com as tabelas servicos e pecas).

6. Serviços:
- Representa os serviços que podem ser realizados na oficina, como troca de óleo, alinhamento, etc.
- Atributos: id_servico (PK), descricao, valor_unitario.
- Relacionamentos: Um serviço pode ser associado a várias ordens de serviço (N:M com a tabela ordem_servico_servicos).

7. Peças:
- Representa as peças utilizadas para realizar os serviços nas ordens de serviço.
- Atributos: id_peca (PK), descricao, valor_unitario.
- Relacionamentos: Uma peça pode ser associada a várias ordens de serviço (N:M com a tabela ordem_servico_pecas).

8. ordem_servico_servicos (Tabela de junção):
- Gerencia o relacionamento muitos-para-muitos entre Ordens de Serviço e Serviços.
- Atributos: id_os (FK), id_servico (FK), quantidade, valor_total.
- Relacionamentos: Relaciona uma ordem de serviço com vários serviços.

9. ordem_servico_pecas (Tabela de junção):
- Gerencia o relacionamento muitos-para-muitos entre Ordens de Serviço e Peças.
- Atributos: id_os (FK), id_peca (FK), quantidade, valor_total.
- Relacionamentos: Relaciona uma ordem de serviço com várias peças. <br><br><br>

## 📈 Diagrama de Entidade-Relacionamento (ER)

O Diagrama de Entidade-Relacionamento (ER) ilustra as entidades do sistema e seus relacionamentos. Você pode visualizar o diagrama visualmente no **MySQL Workbench** após importar o modelo de dados SQL. O diagrama mostra como as tabelas estão interconectadas e a estrutura do banco de dados. <br><br>

## ⚙️ Tecnologias Utilizadas

**MySQL:** Para o banco de dados relacional.

**MySQL Workbench:** Para modelagem de banco de dados e criação do diagrama ER.<br><br>

## 📥 Como Usar
**Requisitos**
- **MySQL** instalado em sua máquina.
- **MySQL Workbench** (opcional, para visualização do diagrama ER).

**Passos**
1. Clone este repositório em seu ambiente local:
git clone https://github.com/seu-usuario/Projeto-Conceitual-de-Banco-de-Dados-Oficina.git

2. Acesse o diretório do projeto:

3. Importe o arquivo SQL para o MySQL:
- Abra o MySQL Workbench.
- Conecte-se ao seu servidor MySQL.
- Execute o script SQL fornecido para criar o banco de dados e as tabelas.

4. Após a execução do script, o banco de dados estará configurado com todas as tabelas e relacionamentos descritos.

