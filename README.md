# 📘 App Api ShowCase

[![Maven Central](https://img.shields.io/maven-central/v/org.springframework.boot/spring-boot-starter.svg?logo=apache-maven)](https://search.maven.org/artifact/org.springframework.boot/spring-boot-starter)
[![Java](https://img.shields.io/badge/Java-21-blue.svg?logo=java)](https://adoptium.net/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.5-brightgreen.svg?logo=springboot)](https://spring.io/projects/spring-boot)
[![Coverage Status](https://img.shields.io/codecov/c/github/ramiralvesmelo/app-api?logo=codecov)](https://app.codecov.io/gh/ramiralvesmelo/app-api)

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=bugs)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=code_smells)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=coverage)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Duplicated Lines (%)](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=duplicated_lines_density)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Lines of Code](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=ncloc)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=reliability_rating)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=security_rating)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Technical Debt](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=sqale_index)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=sqale_rating)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)
[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=ramiralvesmelo_app-api&metric=vulnerabilities)](https://sonarcloud.io/summary/new_code?id=ramiralvesmelo_app-api)

⚠️ Importante: badges referentes ao projeto original

---

# 📘 Sobre o Projeto

O **app-api** é uma aplicação de demonstração de um ERP em pequena escala, criada para estudos e treinamentos. Possui arquitetura modular e utiliza frameworks como: Java 24, Spring Boot 3.3.5, Spring Security, JPA/Hibernate, Spring Cache, Swagger/OpenAPI, JUnit 5 e Mockito.

O projeto também conta com um **workflow de CI/CD** totalmente automatizado no GitHub Actions, responsável por assegurar a **qualidade do código**, manter a **cobertura de testes**, realizar **análises estáticas** como SonarCloud e CodeCov, gerar o SBOM (Software Bill of Materials) e garantir a **entrega contínua** de artefatos e imagens Docker.

![Integração do App Api](infra/img/app-demo-integration.drawio.png)

---

## ⚙️ Pré-requisitos

Antes de começar, certifique-se de ter as seguintes ferramentas instaladas em sua máquina:

* [Docker](https://www.docker.com/get-started) v20.10 ou superior
* [Git Client](https://git-scm.com/downloads) v2.30 ou superior

---

### 📍 Acesso pelo Host (Windows/Linux)

Para acessar o **Keycloak** pelo **nome do serviço** `keycloak` a partir do **host**, adicione a entrada no arquivo *hosts* do sistema:

```text
127.0.0.1   keycloak
```

**Caminhos dos arquivos de hosts:**

* 🪟 **Windows:** `C:\Windows\System32\drivers\etc\hosts`
* 🐧 **Linux:** `/etc/hosts`

> ℹ️ **Nota Importante:** dentro da rede interna do **Docker Compose**, o DNS já resolve automaticamente o nome `keycloak`. A modificação no arquivo *hosts* é necessária apenas para permitir que o **host** acesse `http://keycloak:8081/` — especialmente útil quando o *issuer* do token faz referência a esse endereço.

---

## 🚀 Como Inicializar o Projeto

<video src="app-api.webm" controls width="600"></video>

Abaixo segue um passo a passo para inicializar a API.

### 📥 Clonar o projeto

```bash
git clone https://github.com/ramiralvesmelo/app-api-showcase.git
cd app-api-showcase
```

### 🟢 Subir todos os serviços em segundo plano

```bash
docker compose -f infra/docker/docker-compose.yml up -d
```

### 🔴 Derrubar todos os serviços e containers

```bash
docker compose -f infra/docker/docker-compose.yml down
```

### 📜 Visualizar logs do container principal da aplicação

```bash
docker compose -f infra/docker/docker-compose.yml logs -f app-api
```

---

# 🌐 URLs de Acesso

| Serviço           | URL / Endereço                                                                 | Usuário    | Senha     |
| ----------------- | ------------------------------------------------------------------------------ | ---------- | --------- |
| **app-api**      | [http://localhost:8080](http://localhost:8080)                                 | -          | -         |
| **Swagger UI**    | [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html) | -          | -         |
| **App-audit**     | [http://localhost:8084](http://localhost:8084)                                 | -          | -         |
| **Keycloak**      | [http://localhost:8081](http://localhost:8081)                                 | admin      | admin     |
| **Healthcheck**   | [http://localhost:8080/actuator/health](http://localhost:8080/actuator/health) | -          | -         |
| **PostgreSQL**    | `jdbc:postgresql://localhost:5432/appdb`                                       | appuser    | apppass   |
| **H2**            | `jdbc:h2:mem:testdb`                                                           | sa         | -         |
| **H2 Console**    | [/h2-console](http://localhost:8080/h2-console)                                | sa         | -         |
| **Redis**         | `localhost:6379`                                                               | -          | -         |
| **Redis UI**      | [http://localhost:8082](http://localhost:8082)                                 | admin      | admin     |
| **Kafka**         | `localhost:9092`                                                               | -          | -         |
| **Kafka UI**      | [http://localhost:8083/ui/](http://localhost:8083/ui/)                         | -          | -         |
| **MongoDB**       | `mongodb://mongoadmin:mongopass@localhost:27017/auditdb?authSource=admin`      | mongoadmin | mongopass |
| **Mongo Express** | [http://localhost:8085](http://localhost:8085)                                 | admin      | admin     |
| **Zookeeper**     | `localhost:2181`                                                               | -          | -         |

---

### 🔐 Authorization Code Flow com PKCE (Swagger UI)

```mermaid
sequenceDiagram
  autonumber
  participant U as Usuário
  participant SW as Swagger UI (Cliente Público)
  participant AS as Authorization Server (Keycloak)
  participant RS as API (Resource Server)

  U->>SW: Clica em autenticar
  SW-->>SW: Gera Code Verifier e Code Challenge
  SW->>AS: Envia Authorization Code Request + Code Challenge
  AS->>U: Redireciona para tela de login
  U->>AS: Usuário envia credenciais de autenticação
  AS->>SW: Authorization Server valida credenciais se OK, devolve Authorization Code
  SW->>AS: Swagger UI envia Authorization Code + Code Verifier
  AS-->>AS: Verifica se Code Verifier "bate" com Code Challenge
  AS->>SW: Retorna o Access Token  
  SW-->>RS: 200 OK (dados protegidos)

```

> 💡 **Observações**
>
> * O **Authorization Server** emite um authorization code — um “ticket” de uso único, vinculado ao cliente (e ao redirect_uri), com validade curta (ex.: 30–60 s).

> * No PKCE, o **Code Verifier** é uma string aleatória e secreta gerada no cliente. O **Code Challenge** é derivado do verifier — normalmente `BASE64URL(SHA-256(verifier))`.

> * **COM PKCE** o `client_secret` fica no Authorization Server.

> * **SEM PKCE** o `client_secret` fica no Client.


### 📊 Diagrama Entidade-Relacionamento (MER)

![MER-001](infra/img/mer-001.png)

O diagrama acima representa a relação entre as entidades principais, incluindo chaves primárias e estrangeiras que garantem integridade referencial.

---

## 📨 Mensageria com Kafka

* **`app.kafka.topic.order-finalized`** → Nome do **tópico Kafka** onde serão publicadas as mensagens de pedidos finalizados.
  Exemplo: sempre que um pedido é concluído, uma mensagem é enviada para esse tópico.

* **`spring.kafka.consumer.group-id`** → Identificador do **grupo de consumidores**.
  Todos os consumidores com o mesmo `group-id` compartilham a carga das mensagens do tópico.
  Isso garante **paralelismo** e **balanceamento** — cada mensagem é entregue para apenas um consumidor dentro do grupo.

---

## 🚀 Workflow (GitHub Actions)

Este workflow automatiza as etapas de **CI/CD** para o projeto, contemplando análise de código, cobertura de testes, publicação de pacotes e imagens em repositórios.

### 🔍 CI – Integração Contínua

* 📥 **Checkout** do repositório.
* ⚙️ **Configuração do JDK 24** e cache do Maven.
* 🔎 **Verificação de versões** (Java e Maven).
* 🛠️ **Build + Test + Coverage** com JaCoCo.
* 📈 **Envio do relatório de cobertura** para o Codecov.
* 🔎 **Análise no SonarCloud** com verificação de *Quality Gate*.
* 📦 **Geração do SBOM** (CycloneDX).
* 📤 **Upload do SBOM** como artefato do workflow.
* 📊 **Envio do snapshot de dependências** para o Dependabot/Graph.

### 🚀 CD – Entrega Contínua

* 📥 **Checkout** do repositório.
* ⚙️ **Configuração do JDK 24** e cache do Maven.
* 🔐 **Configuração de credenciais Maven (settings.xml)**.
* 🐈‍⬛ **Deploy no GitHub Packages** (Maven Repository).
* 🧱 **Configuração do Docker Buildx**.
* 🔑 **Login no GHCR** (GitHub Container Registry).
* 🏷️ **Definição de metadados** (tags/labels da imagem Docker).
* 🐈‍⬛ **Build & Push da imagem** no GHCR.
* 🔑 **Login no Docker Hub**.
* 🐋 **Build & Push da imagem** no Docker Hub.


✅ Com esse fluxo, garantimos qualidade de código, rastreabilidade das dependências e entrega automatizada de artefatos e imagens.

---

## 🌱 Fluxo de Branches (GitFlow)

Adotamos o **GitFlow** para organizar entregas e paralelizar trabalho com segurança:

* **`main`**: linha de produção (somente `releases` e `hotfixes` versionados).
* **`develop`**: linha de desenvolvimento contínuo (base para `features`).
* **`feature/*`**: novas funcionalidades ou melhorias curtas, criadas a partir de `develop`.
* **`release/*`**: preparação de versão; estabilização e ajustes finais, criada a partir de `develop`.
* **`hotfix/*`**: correções urgentes em produção, criadas a partir de `main` e integradas de volta em `main` e `develop`.

---

### 🗺️ Gráfico (GitFlow)

```mermaid
gitGraph
   commit id: "v0.1"
   branch develop
   commit
   branch feature/featureA
   commit
   commit
   checkout develop
   merge feature/featureA
   branch feature/featureB
   commit
   commit
   checkout develop
   merge feature/featureB
   branch release/0.2
   commit
   commit
   checkout main
   merge release/0.2 id: "v0.2"
   checkout develop
   merge release/0.2
   branch hotfix/0.2.1
   commit
   checkout main
   merge hotfix/0.2.1 id: "v0.2.1"
   checkout develop
   merge hotfix/0.2.1
   branch release/1.0
   commit
   commit
   checkout main
   merge release/1.0 id: "v1.0"
   checkout develop
   merge release/1.0
```

---

### 📌 Legenda

| Branch       | Função                                                                        |
| ------------ | ----------------------------------------------------------------------------- |
| **main**     | Produção, recebe merges de `release` e `hotfix` com **tags** de versão        |
| **develop**  | Desenvolvimento contínuo, recebe merges de `features`, `release` e `hotfix`   |
| **feature/** | Desenvolvimento de novas funcionalidades a partir de `develop`                |
| **release/** | Preparação de versões, testes e ajustes finais antes de ir para `main`        |
| **hotfix/**  | Correções urgentes criadas a partir de `main`, voltam para `main` e `develop` |

---

## 🗂️ Estrutura do Projeto

```text
app-api/
├── .github/                               		# Configurações do GitHub
│   └── workflows/                         		# Actions (CI)
│       └── maven.yml                      		# Pipeline Maven (build, testes, etc.)
├── infra/                                 		# Infra local e ferramentas
│   ├── docker/                            		# Docker / Compose da stack
│   │   ├── docker-compose.yml             		# Subir app + dependências (Postgres, Kafka, Redis, Keycloak)
│   │   └── Dockerfile                     		# Imagem da aplicação (JDK 21)
│   ├── insonia/                           		# Coleções do Insomnia
│   │   └── app-demo-collection.yaml       		# Requests prontos (inclui auth)
│   ├── jmeter/                            		# Testes de carga/performance
│   │   └── post-customers-10000-random.jmx		# Script exemplo JMeter
│   └── keycloak/                          		# Realm e dados do Keycloak
│       └── realms/		
│           ├── app-demo-realm.json        		# Realm com clients/roles/flows iniciais
│           └── h2/                        		# Base H2 do Keycloak (modo DEV)
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── br/com/springboot/appdemo/ 		# Código-fonte principal
│   │   │       ├── Application.java       		# Classe bootstrap Spring Boot
│   │   │       ├── config/                		# Configurações (Security, Kafka, Transação, Web, etc.)
│   │   │       ├── controller/            		# REST Controllers
│   │   │       ├── exception/             		# Exceções de negócio e handler global
│   │   │       ├── message/               		# Eventos e integração (Kafka)
│   │   │       ├── model/                 		# DTOs e Entidades JPA
│   │   │       ├── repository/            		# Repositórios (interfaces + impl custom)
│   │   │       ├── service/               		# Interfaces e serviços (impl)
│   │   │       └── util/                  		# Utilitários (email, número de pedido, segurança)
│   │   └── resources/		
│   │       ├── application.properties     		# ⚙️ Config padrão (perfil default)
│   │       ├── application-docker.properties 	# ⚙️ Config para perfil `docker`
│   │       ├── schema.sql                 		# DDL inicial (dev/test)
│   │       └── data.sql                   		# Dados de exemplo (dev/test)
│   └── test/		
│       ├── java/                          		# Testes unitários/integração
│       └── resources/
│           └── application-test.properties		# Config de testes
├── .dockerignore
├── .gitignore
├── pom.xml                                		# Projeto Maven
└── README.md                              		# Este arquivo
```

---

## 📊 JMeter – Testes de Carga

```sh
# Linux
rm -rf /temp/jmeter/
mkdir -p /temp/jmeter/

# Windows
Remove-Item -Recurse -Force "/temp/jmeter"
New-Item -ItemType Directory -Path "/temp/jmeter"

# Executar plano de teste
jmeter -n -t post-customers-10000-random.jmx \
  -l /temp/jmeter/results.jtl \
  -e -o /temp/jmeter/report
```
---

## 📜 Licença

Distribuído sob a licença **MIT**. &#x20;
Sinta-se livre para usar, modificar e compartilhar.