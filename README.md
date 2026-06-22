# 🚀 Projeto: Ajuda Lá - Conectando quem sabe a quem precisa

## 📋 Identificação do Projeto
* **Título do Projeto:** Ajuda Lá - Plataforma de Agendamento de Serviços
* **Integrantes da Equipe:**
  * Gabriel Henrique Vilar
  * [Davi Dominicki]
  * Arthur Chrispim Mainardes Ribeiro
* **Curso:** Análise e Desenvolvimento de Sistemas (ADS)
* **Turma:** [Inserir Turma/Semestre]

---

## 📝 Resumo
O **Ajuda Lá** é uma plataforma web desenvolvida para atuar como uma ponte ágil e segura entre cidadãos que necessitam de serviços cotidianos e profissionais autônomos capacitados. Construído sob uma arquitetura de API RESTful em C# (.NET 8) com um banco de dados SQLite, e consumido por uma interface reativa em React, o sistema simplifica a busca por categorias de serviço (como encanadores, eletricistas, etc.). A aplicação oferece fluxos dedicados para Prestadores e Contratantes, garantindo a integridade dos compromissos por meio de uma regra de negócio avançada que previne a sobreposição de agendamentos, e culmina em uma integração fluida com o WhatsApp para a conclusão do atendimento.

---

## ⚙️ Funcionalidades
* **Autenticação e Perfis Direcionados:** Login específico para Administradores, Prestadores e Contratantes.
* **Gestão de Categorias (CRUD):** Painel administrativo protegido para criação e listagem de categorias de ofícios.
* **Catálogo de Profissionais:** Listagem dinâmica de prestadores filtrados pela categoria de serviço desejada pelo cliente.
* **Agendamento Inteligente:** Motor de agendamento com validação de disponibilidade (janela de segurança de 1 hora).
* **Painel de Controle do Profissional:** Página para o prestador visualizar, aceitar ou recusar solicitações de serviço.
* **Integração de Comunicação:** Geração automática de mensagens via WhatsApp (Deep Link) após a confirmação do agendamento.

---

## 🔍 Descrição das Funcionalidades

* **Autenticação e Perfis Direcionados:** O sistema roteia o usuário de acordo com o seu perfil de cadastro. A plataforma possui áreas isoladas para a busca de serviços (Contratante), para a gestão da própria agenda (Prestador) e uma área restrita por senha fixa para a manutenção do sistema (Administrador).
* **Gestão de Categorias (CRUD):** O Administrador possui acesso exclusivo para gerenciar o ecossistema da plataforma, podendo cadastrar novas categorias profissionais com nome e descrição, que refletem instantaneamente no momento do cadastro de novos prestadores.
* **Catálogo de Profissionais:** O Contratante navega por uma interface limpa onde seleciona a categoria da sua necessidade. O sistema faz uma requisição ao banco de dados e retorna os "cards" de todos os prestadores habilitados naquela especialidade.
* **Agendamento Inteligente:** Ao solicitar um serviço, o backend em C# processa uma verificação de conflito de tempo (*time-slot overlap*). O sistema valida o intervalo, bloqueando tentativas de marcar serviços com menos de 1 hora de diferença para o mesmo profissional, garantindo a viabilidade do deslocamento.
* **Painel de Controle do Profissional:** O Prestador tem acesso a uma agenda interativa. Os serviços chegam com o status "Pendente". Ao clicar em Aceitar ou Recusar, o sistema faz um `PUT` na API, atualizando o status visual da etiqueta e liberando ou bloqueando a agenda em tempo real.
* **Integração de Comunicação:** Para facilitar a logística final, assim que um Contratante agenda um horário, o React processa o número de telefone do prestador e aciona a API do WhatsApp Web/Mobile, abrindo uma conversa com uma mensagem pré-formatada contendo os dados do cliente e a data escolhida.

---

## 📂 Repositório
O código fonte completo desta aplicação encontra-se centralizado neste repositório, organizado da seguinte forma:
* **Backend:** Desenvolvido em C# (.NET 8) com Entity Framework Core e SQLite (pasta `AjudaLaServices.Api`).
* **Frontend:** Desenvolvido em React com TypeScript e Axios (pasta `ajudala-frontend`).

---

## 🤖 Uso de IA
Atendendo aos requisitos de desenvolvimento e documentação do projeto, a Inteligência Artificial foi integrada ativamente ao fluxo de trabalho da equipe:

* **Ferramenta utilizada:** Google Gemini.
* **Forma de uso:** * **Planejamento de Arquitetura:** Geração de *boilerplate* (estruturas base) para as rotas em C# e componentes em React.
  * **Resolução de Problemas:** Auxílio no *debugging* de erros de compilação (ex: capitalização de variáveis no Entity Framework) e conflitos no versionamento do Git.
  * **Regras de Negócio:** *Prompts* direcionados para a elaboração de lógica de proteção de endpoints, especificamente o algoritmo de verificação de disponibilidade de agenda (margem de segurança de 1 hora entre os compromissos).
  * **Documentação:** Elaboração da redação técnica dos tópicos "Resumo", "Funcionalidades" e "Descrição das funcionalidades" deste README.
* **Revisões realizadas pela equipe:** Todo o código fornecido pela IA foi auditado e ajustado pela equipe para garantir a compatibilidade com a versão mais recente do .NET (v8.0) e do React Router. As lógicas de validação sugeridas foram testadas manualmente via terminal, e os textos desta documentação sofreram revisão final de coerência e padronização por parte dos desenvolvedores.