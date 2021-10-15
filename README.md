# Introdução Docker

<div style="text-align:center"><img src="https://www.cloudlabs.com.br//wp-content/uploads/2017/07/whale-docker-logo.png" /></div>
![Docker Logo](https://www.cloudlabs.com.br//wp-content/uploads/2017/07/whale-docker-logo.png)

## Containers

- Um container é um padrão de unidade de software que empacota código e todas as dependências de uma aplicação fazendo que a mesma seja executada rapidamente de forma confiável de um ambiente computacional para o outro.

- Como funcionam os containers?
  - **Namespaces**
    
    - Isola os processos e sua hierarquia
    - Containers são processos que são isolados com seus filhos (processos)
    
  -  Processos podem ser de vários tipos
    - PID - processos em si
    - User 
    - Network
    - File system
    
  - Container é um processo com sub processos dele rodando emulando um sistema operacional
  
  - **Cgroups**
  
    - Possibilita o controle de recursos
    - Isola os recursos computacionais dos processos (Containers)
  
  - **File System**
  
    - OFS (Overlay File System)
  
    - Os containers herdam todas as dependências do sistema operacional, tornando ele leve.
  
      
  
- **Imagens**

  - São criadas a partir de camadas

  - Camadas de dependências

  - Existe uma arvore de dependências que possibilitam a execução de um determinado App.

  - Possibilidade de corrigir dependências especificas sem impactar nos demais.

  - Utilizar camadas de dependências que podem ser reutilizadas em diversas outras imagens.

    

- **Dockerfile**

  - Arquivo de definição de imagens
  - Usuário define como será a imagens que será gerada

```
FROM: ImageName
RUN: Comandos ex:apt-get install
EXPOSE:8000
```

​		

Um container tem uma imagem de estado imutável, é rápido por rodar dentro de um processo em tempo real em uma aplicação. Após subir o container é criado uma camada de leitura e escrita que permite alterar o comportamento do container, não é a imagem que está sendo alterada. 

No caso de matar o container tudo que foi escrito será perdido.

Em caso de escrita, através de um commit, é gerada uma outra versão da imagem (v2) onde contemplará as alterações escritas. Com isso, existe duas formas de gerar uma imagem, uma é através do Dockerfile e a outra forma é através de um container que está em execução, escrever dentro dele e através de um commit é gerado uma nova imagem.

- **Image Registry**
  - Atua como um repositório
  - Responsável por armazenar as imagens do usuário
  - Toda vez que é gerado uma nova imagem através do Dockerfile, a ImageName está vindo do Image Registry ou seja é realizado um pull.
  - Após o build de uma nova versão de uma imagem é possível realizar um push da imagem no Image Registry.



## Docker

É uma solução onde é integrado Namespace, Cgroups e File System.

- Docker Host - Disponibiliza uma API para trabalhar com Docker
  - Daemon API
  - Cache - Armazena imagens baixadas do Image Registry para otimizar a criação de containers
  - Volumes - Responsável por possibilitar compartilhamentos externos ao container (Exemplo salvar um arquivo gerado no container em uma pasta no computador)
  - Network -  Garante a comunicação entre os containers
- Docker Client - Necessário pra realizar a comunicação com a API disponibilizada pelo Host
