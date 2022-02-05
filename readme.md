## 📝 Arquitetura Monolítica

Sistema com todas as camadas (Front-end, serviços, banco de dados) integrados dentro da mesma aplicação;

Com as arquiteturas monolíticas, todos os processos são altamente acoplados e executam como um único serviço. Isso significa que se um processo do aplicativo apresentar um pico de demanda, toda a arquitetura deverá ser escalada. A complexidade da adição ou do aprimoramento de recursos de aplicativos monolíticos aumenta com o crescimento da base de código. Essa complexidade limita a experimentação e dificulta a implementação de novas ideias. As arquiteturas monolíticas aumentam o risco de disponibilidade de aplicativos, pois muitos processos dependentes e altamente acoplados aumentam o impacto da falha de um único processo.

![img](https://miro.medium.com/max/700/1*2rasaQ6eYtMolf16LplMLw.png)



![img](https://philcalcado.com/img/2015-09-back-end-for-front-end-pattern/sc-monolith-1.png)

## 📝 Arquitetura Microsserviços

Sistema composto de pequenos serviços independentes que se comunicam usando APIs bem definidas;

Com uma arquitetura de microsserviços, um aplicativo é criado com componentes independentes que executam cada processo do aplicativo como um serviço. Esses serviços se comunicam por meio de uma interface bem definida usando APIs leves. Os serviços são criados para recursos empresariais e cada serviço realiza uma única função. Como são executados de forma independente, cada serviço pode ser atualizado, implantado e escalado para atender a demanda de funções específicas de um aplicativo.

![img](https://miro.medium.com/max/499/1*EFvC-Q21-Qt7JSkDc9z3mg.png)



## 📝 Backend for frontend (BFF)

O Back-end for Front-end (BFF) é um microsserviço que customiza a entrega de back-end para cada interface ou experiência do usuário. Isso é bastante útil quando temos um produto complexo, com diversas interfaces, uma vez que cada uma delas tem uma necessidade específica. Ou seja, é melhor definir serviços de back-end diferentes para cada tipo de cliente front-end. Melhor ainda se cada back-end for desenvolvido por equipes alinhadas com cada front-end para garantir que todas as necessidades sejam atendidas. 

![img](https://miro.medium.com/max/534/1*UxrsyWuuajcL1N-3eXW7bQ.png)





![img](https://philcalcado.com/img/2015-09-back-end-for-front-end-pattern/sc-bff-6.png)





## 📝 Domain-Driven Design (DDD)

E uma filosofia combinada a um Design Patterns (Padrão de Projeto) , sua utilização não é obrigatória, mas é recomendada como um guia para criar uma modelagem com base no negócio.

Domain-Driven Design (DDD) é um conjunto de princípios para projeto de software, organizados e sistematizados em 2003, por Eric Evans, em um livro com o mesmo nome.

Os princípios defendidos por DDD têm, no seu conjunto, um objetivo central: permitir o desenvolvimento de sistemas cujo design é centrado em conceitos próximos e alinhados com um domínio de negócio.

O **domínio** de um sistema consiste da área e problema de negócio que ele pretende resolver.

DDD defende que os **desenvolvedores** devem ter um profundo conhecimento do domínio do sistema que eles desenvolvem. Esse conhecimento deve ser obtido por meio de conversas e discussões frequentes com **especialistas no domínio** (ou no negócio). Portanto, o design do sistema deve ser norteado para atender ao seu domínio. E não, por exemplo, para se moldar a uma determinada tecnologia de programação. Em suma, o design é dirigido pelo domínio, e não por frameworks, arquiteturas, linguagens de programação, etc.

É importante mencionar também que DDD se sobressai quando é usado em sistemas para domínios complexos, cujas regras de negócio são mais difíceis de serem imediatamente entendidas e implementadas pelos desenvolvedores.

#### Linguagem Ubíqua

**Linguagem Ubíqua** (ou **Linguagem Onipresente**) é um conceito central de DDD. Ela consiste de um conjunto de termos que devem ser plenamente entendidos tanto por especialistas no domínio (usuários do sistema) como por desenvolvedores (implementadores do sistema).

Para um projeto de software dar certo, DDD defende que esses dois papéis – especialistas no domínio e desenvolvedores – devem falar a mesma língua, que vai constituir a chamada Linguagem Ubíqua do sistema. Essa ideia é ilustrada na seguinte figura:

![A linguagem ubíqua representa o conhecimento compartilhado entre especialistas do negócio e desenvolvedores.](https://engsoftmoderna.info/artigos/figs/linguagem-onipresente.svg)



A figura deixa claro que existem termos que só os especialistas de domínio conhecem. Já outros termos, de cunho tecnológico, são do conhecimento apenas dos desenvolvedores. Porém, existe um conjunto de termos que devem ser do conhecimento de ambos, os quais formam a Linguagem Ubíqua do sistema.

Os termos da Linguagem Ubíqua são usados com dois propósitos:

- Para possibilitar uma comunicação fluida entre desenvolvedores e especialistas no domínio.
- Para nomear entidades do código do sistema, como classes, métodos, atributos, pacotes, módulos, tabelas de bancos de dados, rotas de APIs, etc.

Além de clarificar o significado dos termos da linguagem ubíqua, é importante que se definam os **relacionamentos** e **associações** que existem entre eles.

#### Objetos de Domínio

DDD foi proposto pensando em sistemas implementados em linguagens orientadas a objetos. Então, quando se define o design desses sistemas, alguns tipos importantes de objetos se destacam. Dentre eles, DDD lista os seguintes:

- Entidades
- Objetos de Valor
- Serviços
- Agregações
- Repositórios

Esses tipos de objetos de domínio devem ser entendidos como as ferramentas conceituais que um projetista deve lançar mão para projetar com sucesso um determinado sistema. Por isso, eles são chamados também dos **building blocks** de DDD. Iremos comentar sobre cada um deles a seguir.

**ENTIDADE:** Uma **entidade** é um objeto que possui uma identidade única, que o distingue dos demais objetos da mesma classe. 

**OBJETOS DE VALOR:** (*value objects*) não possuem um identificador único. Assim, eles são caracterizados apenas por seu estado, isto é, pelos valores de seus atributos. Exemplos de objetos de valor incluem: `Moeda`, `Data`, `Fone`, `Email`, `Hora`, `Cor`, etc.

**SERVIÇOS:**  Existem operações importantes do domínio que não se encaixam em entidades e objetos de valor. Assim, o ideal é criar objetos específicos para implementar essas operações. No jargão de DDD, esses objetos são chamados de **serviços**. Em alguns sistemas, é comum ver esses objetos sendo chamados também de gerenciadores ou controladores.

**AGREGADOS (*aggregates*):** São coleções de entidades e objetos de valor. Ou seja, algumas vezes não faz sentido raciocinar sobre entidades e objetos de valor de forma individual. Em vez disso, temos que pensar em grupos de objetos para ter uma visão consistente com o domínio que estamos modelando. Um agregado possui um objeto raiz, que deve ser uma entidade. Externamente, o agregado é acessado a partir dessa raiz. A raiz, por sua vez, referencia os objetos internos do agregado. Porém, esses objetos internos não devem ser visíveis para o resto do sistema, ou seja, apenas a raiz pode referenciá-los.

Como formam uma unidade coerente, agregados são persistidos em conjunto em bancos de dados. A deleção de um agregado, da memória principal e/ou de um banco de dados, implica na deleção da sua raiz e de todos os objetos internos.

**REPOSITÓRIO:** Um objeto usado para recuperar outros objetos de domínio de um banco de dados. Seu objetivo é prover uma abstração que blinde os desenvolvedores de preocupações relacionadas com acesso a bancos de dados. Normalmente, repositórios são criados para recuperar entidades ou agregados.

Em outras palavras, um repositório oferece uma abstração para o banco de dados usado pelo sistema e, assim, permite que os desenvolvedores continuem focados no domínio, em vez de ter sua atenção desviada, em certos momentos, para uma tecnologia de armazenamento de dados. Em termos mais concretos, um repositório permite manipular objetos de domínio como se eles fossem listas (ou coleções) armazenadas na memória principal. A implementação interna do repositório cuida então de ler e salvar essas listas no banco de dados.



## 📝 TEST-DRIVEN DEVELOPMENT (TDD)

TDD significa Desenvolvimento Orientado por Testes (Test Driven Development), e trata-se de uma prática de desenvolvimento de software onde a codificação das funcionalidades começa a partir da escrita de testes unitários. Essa técnica foi criada por Kent Beck e é um dos pilares do XP (Extreme Programming).

![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--b9FjzOmj--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5ryscmqtvkgmbh6ihg3k.gif)



O TDD consistem em um ciclo apelidado de Red, Green, Refactor. Que funciona da seguinte maneira:

1. Escrevemos um teste para uma funcionalidade a qual queremos implementar. Ao executar esse teste ele deve falhar, pois ainda não temos a implementação e assim passamos pelo step red.
2. Após o nosso teste falhar implementamos a funcionalidade e executamos o nosso teste novamente, porém dessa vez o teste passa com sucesso, com isso passamos pelo step green do TDD.
3. Com os testes funcionando chegamos ao step refactor. Como o próprio nome já diz, nesse momento devemos refatorar nosso código procurando pontos a melhorar e aplicando boas práticas de programação.

Esse ciclo pode se repetir quantas vezes o desenvolvedor julgar necessário e a cada nova implementação é interessante que todos os testes que já estão em funcionamento sejam executados, pois assim é possível validar que todos os testes continuam funcionando e que a nova implementação não impactou nas funcionalidades já desenvolvidas.

Os principais benefícios do TDD são:

- Maior cobertura de testes unitários
- Testes são executados com maior frequência
- O código se torna mais limpo



## 📝 BEHAVIOR-DRIVEN DEVELOPEMENT (BDD)

Em tradução livre, BDD é Desenvolvimento Orientado ao Comportamento.

BDD é uma técnica de desenvolvimento de software ágil, criado por Dan North, em 2003, com o intuito de melhorar a comunicação entre um time de desenvolvimento (PO, QA e DEV) para que todos tenham o mesmo entendimento sobre uma determinada funcionalidade.

O BDD foi criado em resposta a problemas que Dan North presenciava através do uso da técnica do TDD – Test Driven Development (Desenvolvimento orientado a testes). A maioria dos times de desenvolvimento e seus alunos tinham dificuldade em como escrever seus testes de acordo com uma determinada User Story. 

Então, surge o BDD trazendo a proposta que cenários serão escritos exemplificando comportamentos de uma funcionalidade para que a mesma atinja um objetivo real, agregando valor ao negócio, e assim, dando um suporte ao TDD para que os testes sejam feitos de acordo com os cenários que foram descritos. 

#### O BDD apresenta um framework baseado em três princípios

- A área de negócios e o time de desenvolvimento precisam se referir a mesma parte do sistema da mesma forma;
- Toda parte do sistema precisa ter um valor identificável e verificável para o negócio;
- Analisar, projetar e planejar tudo de cima a baixo tem retorno decrescente;

Podemos definir o BDD como a união de várias práticas consideradas ágeis e úteis no desenvolvimento de software, cuja ênfase está nas **funcionalidades de alto valor e na redução dos custos de mudança** por meio da identificação do que de fato está sendo testado/desenvolvido.

O BDD nada mais é do que o processo como um todo, um processo de descoberta, o processo que visa entender como uma aplicação irá funcionar. Isso tudo ocorrendo de forma compartilhada e colaborativa entre os membros da equipe de desenvolvimento, onde discutirão uma funcionalidade e escreverão cenários, utilizando uma DSL chamada Gherkin(Given/When/Then), exemplificando assim, o caminho que o usuário irá executar em tal aplicação e o comportamento esperado por ele. 

Automatizar esses cenários não é uma obrigação, e sim, uma opção. O BDD deverá ser um ponto de partida para poder entender como o sistema deve se comportar e assim, pensar em formas mais robustas de testes automatizados, seja fazendo um TDD, automatizando camadas de front-end ou mesmo realizando testes automatizados de uma API. 

![BDD Behaviour Driven Software Development](https://www.q-perior.com/wp-content/uploads/2020/03/BDD_behaviour-driven-software-development-1920x1120.jpg)

#### BDD na prática

O processo de desenvolvimento do BDD se baseia na escrita de **cenários** de testes. Cada cenário é um exemplo escrito para ilustrar um aspecto específico de comportamento esperado da aplicação. 

Para a escrita do BDD utilizamos uma DSL conhecida como Gherkin, sendo uma linguagem estruturada que se inicia com a sintaxe Given, When e Then (Dado que, Quando, Então). 

- A cláusula *‘Dado’* descreve as condições e pré-condições; 
- Já cláusula *‘Quando’*, tem o objetivo de descrever um evento ou uma ação;
- A cláusula *‘Então’*, trata-se de todas as saídas e resultados esperados, descrevendo as informações visíveis ao usuário ou sistemas externos. 

A seguir temos exemplos de boas práticas na construção de cenários de um BDD: 

#### Exemplo:

**Feature:** Compra de produtos 

**Como** lojas americanas

**Eu quero** permitir frete grátis para clientes

**Para** compra acima de R$100,00 de modo que o cliente seja estimulado a comprar mais.

 

**Cenário:** Permitir frete grátis para clientes que realizam compras acima de R$100,00 

**Dado** que eu esteja realizando uma compra de no mínimo R$100,00 

**Quando** o cliente calcular seu frete 

**Então** será exibido que ele terá o frete grátis para seu pedido 



#### 🤝 Contribuindo

Este repositório foi criado para fins de estudo, então contribua com ele.<br>
Se te ajudei de alguma forma, ficarei feliz em saber. E caso você conheça alguém que se identidique com o conteúdo, não deixe de compatilhar.

Se possível:

⭐️  Star o projeto

🐛 Encontrar e relatar issues


------------

Disponibilizado por [thalysson-borges](https://www.linkedin.com/in/thalysson-borges/ "thalysson-borges").

#### fontes:
https://medium.com/tech-tajawal/backend-for-frontend-using-graphql-under-microservices-5b63bbfcd7d9
https://medium.com/digitalproductsdev/arquitetura-bff-back-end-for-front-end-13e2cbfbcda2
https://philcalcado.com/2015/09/18/the_back_end_for_front_end_pattern_bff.html
https://engsoftmoderna.info/artigos/ddd.html
https://dev.to/womakerscode/o-que-e-tdd-4b5f
https://www.dtidigital.com.br/blog/bdd-como-metodologia-agil/
https://www.q-perior.com/en/blog/behavior-driven-development-when-everyone-speaks-the-same-language/



