# AWS RDS (Relational Database Storage)
 ## Estudo sobre o RDS da amazon
=======================
# Características Gerais

Automatiza diversos processos da criação e administração do banco de dados, prevenindo
    perdas, faz backups automaticamentes e tem um sistema de failover também automatizado.
    Trabalha predominantemente com banco de dados **relacionais** (MySql, Oracle etc).
    Pode-se alterar a escala da sua instância conforme a necessidade


=============================
## Preços

   Os preços do RDS variam conforme o uso e conforme o tipo de banco de dados utilizado  
   E o valores são mensais.
   
=============================

# Tiers do RDS (Relational Database Storage)

## Uso Geral:

### T3:
   O T3 são os hardwares mais agressivos e necessários para aplicações mais pesadas, como banco de dados não relacionais.
   Utiliza o AWS Nitro. 
   Ficasm disponível independente do saldo, apenas será acrescido um valor por hora quando o saldo de uso acabar.
    
### T2:
   Ficam Insdisponíveis se o saldo acabar, tem recursos de hardware mais limitados.

### M5:

   **OBS: M5 difere dos T3 no que diz respeito a flexibilidade, o T3 é mais escalável, logo, para aplicações que não são constantes
   é recomendável o seu uso. o M5 é contante.**
   É otimizado por padão para o EBS e perfeito para aplicações de médios e pequeno porte.
    
### M4:

   É otimizado por padão para o EBS e perfeito para splicações de médios e pequeno porte.

=================================

## Otimizado para memória

### R5:

As instâncias R5 são instâncias última geração otimizadas para memória, que disponibilizam 5% de memória por vCPU a mais que as R4, sendo o maior tamanho capaz de disponibilizar 768 GiB de memória. Além disso, as instâncias R5 oferecem um aprimoramento de preço de 10% por GiB e um aumento de performance de CPU de aproximadamente 20% em relação às instâncias R4.

### R4:

As instâncias R4 são otimizadas para cargas de trabalho de bancos de dados com uso intensivo de memória e oferecem um preço por GiB de RAM melhor que as instâncias R3.

### X1e:

As instâncias X1e são otimizadas para bancos de dados de alta performance. As instâncias X1e oferecem um dos menores preços por GiB de RAM entre os tipos de instância do Amazon RDS.

### X1:

As instâncias X1 são otimizadas para aplicativos em memória, de grande escala e nível empresarial, e oferecem um dos menores preços por GiB de RAM entre os tipos de instância do Amazon RDS.

### Z1d:
 
 As instâncias z1d oferecem uma frequência sustentada em todos os núcleos de até 4,0 GHz. A combinação de alta performance de computação e grande quantidade de memória torna as instâncias z1d ideais para cargas de trabalho de banco de dados relacional com altos custos de licenciamento por núcleo.

=================================================

# AWS BACKUP

 O serviço de backup da Amazon automatiza e centraliza todo o processo de backup em apenas um lugar.
 É integrado com o RDS (Relational Database Storage), EBS(Elastic Block Storage), Amazon DynamoDB, EFS(Elastic File System), AWS STORAGE GATEWAY.

## PREÇO

 A definição de preço do armazenamento do AWS Backup é baseada na quantidade de espaço de armazenamento consumida pelos dados do backup. Para o primeiro backup de um recurso da AWS, uma cópia completa dos dados é salva. Para cada backup incremental, somente a parte alterada do volume do recurso da AWS é salva.

==================================================

# AWS ECS(Elastic Container Service)

O ECS é um serviço de gerenciamento de containers altamente dimensionável, muito usado para integrar o docker com os serviços da AWS.
Possível fazer a integração com o EC2. 
Amazon ECS elimina a necessidade de operar os próprios sistemas de gerenciamento de cluster e de configuração ou de se preocupar com a escalabilidade da infraestrutura de gerenciamento.
Para que o seu container execute determinados comandos, usando uma ferramenta chamada  definição de tarefa (*É um arquivo do tipo Package. JSON, até o máximo de dez, que compõem seu aplicativo*).
As definições de tarefas especificam vários parâmetros para seu aplicativo. 
Exemplos de parâmetros de definição de tarefas são:
  **os contêineres e o tipo de inicialização a serem usados, as portas que devem ser abertas para seu aplicativo e os volumes de dados que devem ser usados com os contêineres nao tarefa**    
Utiliza o Fargate para executar e gerenciar o cluster de containers.

## Preço

Com o AWS Fargate, **não há pagamentos adiantados e você paga apenas pelos recursos que utiliza**. 
Você paga pela quantidade de recursos de vCPU e memória consumidos por seus aplicativos conteinerizados.

A definição de preço é por segundo com o mínimo de um minuto. 
A duração é calculada do momento em que o download da imagens de contêiner (pull do docker) é iniciado até o término da tarefa, arredondado para o segundo mais próximo.

================================================================

# S3 (Amazon Simple Storage Service)
O S3 é uma serviço de banco de Dados escalável na nuvem que cria e armazena automaticamente cópias de todos os objetos do S3 em vários sistemas.
Além disso, cria diversos modelos de controle e criptografia, divide os registros em buckets para ter uma maior rastreabilidade dos dados

## Casos de Uso
  - Backup e Restauração
  - Disaster Recovery (Recuperação de desastres)
  - Arquivamento
  - Analise de data Lakes e Big Data
  - Armazenamento em nuvem híbrida
  - **NUUUUUVEMMMMMM**

## Classes de Armazenamento do S3

- S3 Standard
    - Performance com baixa latência e alto throughput
    - Altamente adaptável e **Ressiliente**
    - Permite migração para outras classes de armazenamento do S3

- S3 Intelligent-Tiering
    - A mesma performance de baixa latência e alto throughput da categoria S3 Standard
    - Pequena taxa mensal de monitoramento e **divisão automática** em níveis (Trabalha em 2 niveis, Um deles é otimizado para um acesso frequente porém é mais caro, e outro projetado para um acessos não tão frequente, porém com um custo mais baixo)
- S3 Standart-Infrequent Access
    - Mano é igualzinho a porra do Standart
    - Porém, recomendado para acessos menos frequentes.
    - A combinação de baixo custo e alta performance tornam a classe S3 Standard-IA ideal para armazenamento de longa duração, backups e datastores para arquivos de recuperação de desastres. As classes de armazenamento S3 podem ser configuradas no nível do objeto, e um único bucket pode conter objetos armazenados no S3 Standard, S3 Intelligent-Tiering, S3 Standard-IA e no S3 One Zone-IA.
- S3 One Zone-Infrequent Access (S3 One Zone-IA)
    - Diferentemente das anteriores, essa classe armazena dados em apenas uma instância, porém com 20% menos custo
    - Recomendado para um uso de pouca frequencia.
- S3 Glacier (Arquivamento)
    Ideal para guardar as paradas chatas, barato dependendo do que for ser utilizado para retirar os dados do arquivamento  
- S3 Glacier Deep Archive
    -  É a  classe de armazenamento mais barata da Amazon
    -  Guarda dados por um grande periodo de tempo
    -  De resto, igual o standard

==========================================================================================

# EC2(Elastic Compute Cloud)


## ECS2

    O EC2 é um serviço que ofere máquinas virtuais, rompendo os limites do hardware físico
    É possível ainda, configurar um volume volátil ou persistente(ebs), criar redes e servidores, firewalls etc.

## Tipos de InstÂncias para o EC2  

 ## Instâncias de uso geral
  - A1: Processador AWS Graviton, Otimizado para EBS, alto desempenho de rede
    Casos de uso (microsserviços em container, servidores web).  
      - A1 Medium
      - A1 Large
      - A1 XLarge
      - A1 2XLarge
      - A1 4xLarge

  - T3: Modo ilimitado, AWS Nitro System, alto desempenho de rede, Otimizado para EBS
    Casos de uso (microsserviços em container, banco de dadosde pqueno e medio).  
      - T3 Nano
      - T3 Micro
      - T3 Small
      - T3 Meidum
      - T3 Large
      - T3 XLarge
      - T3 2XLarge

  - T3a: Modo ilimitado, AWS Nitro System, alto desempenho de rede, Otimizado para EBS
    Casos de uso (microsserviços em container, banco de dadosde pqueno e medio).  
      - T3a Nano
      - T3a Micro
      - T3a Small
      - T3a Meidum
      - T3a Large
      - T3a XLarge
      - T3a 2XLarge

  - T2: Modo intel Xeon, alto desempenho de rede, Otimizado para EBS
    Casos de uso (microsserviços em container, banco de dadosde pqueno e medio).  
      - T2 Nano
      - T2 Micro
      - T2 Small
      - T2 Meidum
      - T2 Large
      - T2 XLarge
      - T2 2XLarge



 ----------------------------

 ## Otimizado para computação
  - Mais processamento

## Otimizado para memória
  - Mais capacidade de RAM
  - 
## Computação Acelerada
  - GPU FUDIDA
## Otimizada para Armazenamento
  - Mais Cpacidade de armazenamento
