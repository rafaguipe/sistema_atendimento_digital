# Sistema de Atendimento Digital
## Exemplo contendo funcionalidades básicas para uma unidade ou sistema de saúde

### 📌 Descrição

Este projeto implementa um sistema de atendimento digital para sistema de saúde, substituindo o uso desorganizado de aplicativo de mensagens por um fluxo estruturado com:

* registro de solicitações
* controle de fila de atendimento
* acompanhamento em tempo real pelo usuário
* painel de gestão para atendentes

---

## 🎯 Objetivo

Resolver o problema de:

* excesso de mensagens
* perda de solicitações
* falta de organização no atendimento
* ausência de rastreabilidade

---

## 🧱 Arquitetura

```text
Usuário (Web)
        ↓
Frontend HTML (Usuário)
        ↓
Node-RED (API REST)
        ↓
Persistência (contextStorage local)
        ↓
Frontend HTML (Painel da Secretaria)
```

---

## ⚙️ Tecnologias Utilizadas

* Node-RED (backend)
* JavaScript (lógica)
* HTML/CSS (frontend)
* REST API
* Context Storage (persistência local)

---

## 🚀 Funcionalidades

### 👤 Usuário

* envio de solicitação (nome, telefone, mensagem)
* geração de protocolo automático
* acompanhamento de status:

  * novo
  * atendendo
  * finalizado
* atualização automática
* persistência do telefone no navegador

---

### 🏥 Sistema de saúde

* visualização em formato Kanban:

  * novos
  * em atendimento
  * finalizados
* ações:

  * iniciar atendimento
  * finalizar atendimento
* atualização em tempo real
* contador de atendimentos ativos

---

## 🔌 Endpoints da API

### 📥 Criar atendimento

```http
POST /whatsapp
```

**Body:**

```json
{
  "nome": "Fulano",
  "telefone": "11999999999",
  "mensagem": "quero consulta"
}
```

---

### 📊 Listar fila (kanban)

```http
GET /fila
```

**Resposta:**

```json
{
  "novos": [],
  "atendendo": [],
  "finalizados": []
}
```

---

### 📂 Atendimentos em aberto por usuário

```http
GET /abertos?telefone=11999999999
```

---

### ▶️ Iniciar atendimento

```http
POST /atender
```

---

### ✅ Finalizar atendimento

```http
POST /finalizar
```

---

## 🧠 Regras de Negócio

### 🔒 Controle de duplicidade

* Um usuário (telefone) não pode ter mais de um atendimento aberto

---

### 📞 Padronização de telefone

Todos os telefones são normalizados:

```javascript
tel.replace(/\D/g, '')
```

---

### 📌 Classificação automática

Mensagens são classificadas em:

* consulta
* exame
* retorno
* outros

---

## 💾 Persistência

O sistema utiliza:

```javascript
contextStorage: localfilesystem
```

✔ dados persistem após reinicialização
❌ não é banco relacional

---

## 🖥️ Interfaces

### 1. Painel da Secretaria

* layout kanban
* atualização automática
* controle de fluxo

---

### 2. Interface do Usuário

* envio de solicitação
* visualização de protocolo
* acompanhamento em tempo real

---

## 🔐 Considerações de Segurança

* isolamento de dados por telefone
* não exibe dados de outros usuários
* validação básica de entrada

---

## ⚠️ Limitações

* não possui autenticação
* não utiliza banco de dados estruturado
* não possui controle de usuários administrativos
* dependente de memória persistida em arquivo

---

## 🔄 Melhorias Futuras

* integração com WhatsApp API
* autenticação de usuários
* banco de dados (PostgreSQL / SQLite)
* geração de protocolo oficial
* notificações em tempo real
* dashboard analítico
* versão mobile (Flutter)

---

## 📦 Como Executar

1. Instalar Node-RED
2. Configurar `contextStorage` para `localfilesystem`
3. Importar os fluxos
4. Iniciar servidor
5. Editar os números de IP:porta nos arquivos html
6. Abrir interfaces HTML

---

## 💡 Insight do Projeto

Este sistema transforma:

❌ atendimento caótico via WhatsApp
➡️
✅ fluxo estruturado com rastreabilidade

---
## Youtube
[Como funciona este sistema](https://youtu.be/Mt_wsOmEtYQ)


---
## 👨‍💻 Autor

Projeto desenvolvido por Rafael Guimarães Pereira como exemplo de implementação ágil.


