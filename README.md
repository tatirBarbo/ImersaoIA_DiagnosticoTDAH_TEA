# Sistema de Apoio Inicial ao Diagnóstico de TDAH e TEA para Pais
Projeto criado na imersao IA da Alura com o Google. 

##Objetivo do Projeto
Este projeto tem como objetivo fornecer um sistema de apoio inicial para pais e responsáveis que desejam obter uma avaliação preliminar sobre a possibilidade de seus filhos apresentarem Transtorno de Déficit de Atenção e Hiperatividade (TDAH) ou Transtorno do Espectro Autista (TEA). O sistema utiliza agentes de inteligência artificial para coletar informações relevantes, gerar questionários e fornecer uma análise inicial baseada nas respostas fornecidas.

* Importante: Este sistema não substitui uma avaliação diagnóstica profissional realizada por médicos e especialistas. Ele serve como uma ferramenta inicial para auxiliar na identificação de possíveis sinais e sintomas, incentivando a busca por acompanhamento especializado quando necessário.

##Utilidade na Vida Real
O sistema pode ser útil em diversas situações:

* Identificação Precoce: Auxilia pais e responsáveis a identificarem precocemente comportamentos e características que podem indicar TDAH ou TEA.
* Orientação Inicial: Fornece uma orientação inicial sobre a probabilidade da criança apresentar o transtorno, ajudando a direcionar a busca por ajuda profissional.
* Preparação para Consulta Médica: Ao utilizar o sistema, os pais podem chegar à consulta médica com informações mais organizadas e claras sobre os comportamentos observados na criança.
* Acesso Facilitado: Em regiões com acesso limitado a especialistas, o sistema pode oferecer um primeiro ponto de contato e informação.

#Explicação Passo a Passo do Código
O código é estruturado em Python e utiliza a biblioteca google-genai e o framework ADK de agentes do Google para criar um sistema de apoio ao diagnóstico. Abaixo, detalhamos as principais partes do código:

Instalação de Bibliotecas:

%pip -q install google-genai: Instala a biblioteca google-genai para interagir com os modelos Gemini.
!pip install -q google-adk: Instala o framework ADK para criação e gerenciamento de agentes.
Configuração da API Key:

Importa as bibliotecas os e google.colab.userdata.
os.environ["GOOGLE_API_KEY"] = userdata.get('GOOGLE_API_KEY'): Configura a chave da API do Google Gemini, obtida através do google.colab.userdata (ferramenta do Google Colab para armazenar dados sensíveis).
Configuração do Cliente Gemini:

Importa a biblioteca google.genai.
client = genai.Client(): Inicializa o cliente para interagir com o modelo Gemini.
MODEL_ID = "gemini-2.0-flash": Define o modelo Gemini a ser utilizado.
Funções Auxiliares:

call_agent(agent: Agent, message_text: str) -> str: Função que envia uma mensagem para um agente, executa o agente e retorna a resposta final. Ela cria um serviço de sessão, um runner para o agente e itera pelos eventos retornados pelo agente para construir a resposta.
to_markdown(text): Função que formata o texto para exibição em Markdown no Colab, facilitando a leitura das respostas dos agentes.

#Agentes:

##Agente Coletor (agente_coletor):
* Objetivo: Coletar informações relevantes sobre TDAH ou TEA no Google, de acordo com o tipo de transtorno e a idade da criança.
* Funcionamento: Utiliza a ferramenta google_search para buscar informações atualizadas sobre características e comportamentos associados ao transtorno especificado.
* Entrada: Tipo de transtorno (1 para TDAH, 2 para TEA), idade da criança e data atual.
* Saída: Informações coletadas sobre o transtorno.
----
##Agente Questionador (agente_questionador):
* Objetivo: Gerar um questionário com perguntas relevantes para auxiliar no diagnóstico do transtorno.
* Funcionamento: Utiliza as informações coletadas pelo agente_coletor e a ferramenta google_search para formular perguntas e classificá-las por relevância.
* Entrada: Tipo de transtorno, idade da criança e informações coletadas.
* Saída: Um questionário com as 10 perguntas mais relevantes.
----
##Agente Avaliador (agente_avaliador):
* Objetivo: Analisar as respostas fornecidas ao questionário e fornecer uma avaliação preliminar da probabilidade da criança ter o transtorno.
* Funcionamento: Avalia as respostas, considerando a relevância das perguntas, e gera um resumo da análise, a conclusão e uma estimativa da probabilidade de acerto.
* Entrada: Tipo de transtorno, idade da criança, questionário e respostas ao questionário.
* Saída: Uma análise preliminar com a probabilidade de a criança ter o transtorno.

#Fluxo Principal do Programa:

Obtém a data atual.
Apresenta uma mensagem de boas-vindas.
Solicita ao usuário o tipo de transtorno (TDAH ou TEA) ou a opção de sair.
Solicita a idade da criança.
Chama o agente_coletor para obter informações sobre o transtorno.
Chama o agente_questionador para gerar o questionário.
Exibe o questionário para o usuário.
Solicita ao usuário que responda às perguntas do questionário.
Chama o agente_avaliador para analisar as respostas e fornecer uma avaliação preliminar.
Exibe a avaliação para o usuário.
Agradece ao usuário e finaliza o programa.

#Conclusão
Este sistema de apoio inicial ao diagnóstico de TDAH e TEA utiliza agentes de inteligência artificial para fornecer uma ferramenta útil para pais e responsáveis. No entanto, é crucial enfatizar que ele não substitui a avaliação de um profissional de saúde qualificado. Seu objetivo é auxiliar na identificação de possíveis sinais e sintomas e orientar a busca por ajuda especializada.  
