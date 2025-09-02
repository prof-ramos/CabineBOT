ChatGPT Discord Bot

Construa seu próprio bot do Discord com múltiplos provedores de IA

⸻

[!IMPORTANTE]

Grande Refatoração (07/2025):
	•	5 Provedores de IA: Gratuito (g4f), OpenAI, Claude, Gemini, Grok
	•	Sem Autenticação via Cookie: Removida a autenticação baseada em cookies para provedores gratuitos (considerada instável)

Chat

Configuração

Pré-requisitos
	•	Python 3.9 ou superior
	•	Renomear o arquivo .env.example para .env
	•	Rodar pip3 install -r requirements.txt para instalar as dependências
	•	Opcional: Chaves de API para provedores premium (OpenAI, Claude, Gemini, Grok)

⸻

Passo 1: Criar um bot no Discord
	1.	Vá em https://discord.com/developers/applications e crie uma aplicação
	2.	Crie um bot dentro da aplicação
	3.	Pegue o token nas configurações do bot

	4.	Guarde o token no .env em DISCORD_BOT_TOKEN

<img height="190" width="390" alt="image" src="https://user-images.githubusercontent.com/89479282/222661803-a7537ca7-88ae-4e66-9bec-384f3e83e6bd.png">



	5.	Ative a opção MESSAGE CONTENT INTENT (ON)

	6.	Convide seu bot para o servidor usando o OAuth2 URL Generator

Passo 2: Rodar o bot no desktop
	1.	Abra um terminal ou prompt de comando
	2.	Navegue até o diretório onde instalou o ChatGPT Discord Bot
	3.	Execute python3 main.py ou python main.py

⸻

Passo 2: Rodar o bot com Docker
	1.	Construa a imagem Docker e rode o container com docker compose up -d
	2.	Verifique se o bot está funcionando com docker logs -t chatgpt-discord-bot
Parar o bot:
	•	docker ps para listar serviços em execução
	•	docker stop <BOT CONTAINER ID> para parar o bot

Bom chat!

⸻

Configuração de Provedores

Provedor Gratuito (instável)

Modelo desatualizado, próximo às capacidades do GPT-3.5 ou GPT-4

Não requer configuração

Provedores Premium (Opcional)

OpenAI
	1.	Pegue sua chave de API em https://platform.openai.com/api-keys
	2.	Adicione no .env: OPENAI_KEY=sua_chave

Claude (Anthropic)
	1.	Pegue sua chave em https://console.anthropic.com/
	2.	Adicione no .env: CLAUDE_KEY=sua_chave

Gemini (Google)
	1.	Pegue sua chave em https://ai.google.dev/
	2.	Adicione no .env: GEMINI_KEY=sua_chave

Grok (xAI)
	1.	Pegue sua chave em https://x.ai/api
	2.	Adicione no .env: GROK_KEY=sua_chave

Use o comando /provider no Discord para alternar entre provedores disponíveis

Geração de Imagens

<img src="https://i.imgur.com/Eo1ZzKk.png" width="300" alt="image">


Agora integrado ao sistema de provedores:

OpenAI DALL-E 3
	•	Requer chave da OpenAI
	•	Geração de imagens de alta qualidade
	•	Use /draw [prompt] openai

Google Gemini
	•	Requer chave da Gemini
	•	Possui camada gratuita
	•	Use /draw [prompt] gemini

Opções de fallback
	•	Se provedores premium não estiverem disponíveis, o bot tentará usar alternativas gratuitas
	•	Capacidades variam conforme o provedor

Opcional: Definir system prompt
	•	O system prompt é chamado quando o bot inicia ou é resetado
	•	Configure editando o conteúdo em system_prompt.txt
	•	O texto será usado como prompt inicial
	•	Para receber a primeira mensagem no seu canal do Discord:
	•	Ative o developer mode nas configurações do Discord
	•	Clique com botão direito no canal → Copy ID
	•	Cole no .env em DISCORD_CHANNEL_ID

Opcional: Desabilitar logging
	•	No .env, defina LOGGING=False

Comandos

Comandos principais
	•	/chat [mensagem] - Conversa com o provedor atual
	•	/provider - Alterna entre provedores (Gratuito, OpenAI, Claude, Gemini, Grok)
	•	/draw [prompt] [modelo] - Gera imagens com o provedor escolhido
	•	/reset - Limpa histórico de conversa
	•	/help - Lista comandos disponíveis

Comandos de persona
	•	/switchpersona [persona] - Troca a personalidade do bot (algumas apenas para admin)
	•	standard - Assistente padrão
	•	creative - Respostas mais criativas
	•	technical - Respostas técnicas e precisas
	•	casual - Tom casual e amigável
	•	jailbreak-v1 - BYPASS (somente admin)
	•	jailbreak-v2 - SAM mode (somente admin)
	•	jailbreak-v3 - Developer Mode Plus (somente admin)

Comportamento do bot
	•	/private - Responde apenas ao usuário que digitou o comando
	•	/public - Responde para todos (padrão)
	•	/replyall - Responde a todas as mensagens do canal (toggle)

Segurança

Jailbreaks apenas para administradores
	1.	Configure ADMIN_USER_IDS no .env com IDs dos administradores
	2.	Apenas administradores podem acessar personas de jailbreak
	3.	Usuários comuns só veem personas seguras

Aviso
Personas de jailbreak podem gerar conteúdo sem filtros de segurança. Acesso restrito a administradores.

Segurança de ambiente
	•	Sem autenticação baseada em cookies (removida por confiabilidade)
	•	Chaves de API seguras via variáveis de ambiente
	•	Docker endurecido para rodar como usuário não-root