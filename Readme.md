# RabbitMQ
  Executando o container:

    docker-compose up ou
    docker-compose up -d

### Rabbit UI

    URL: http://localhost:15672
    User: rabbitmq (olhar docker-compose)
    Password: rabbitmq (olhar docker-compose)

### Conceitos:

    # Simulador de comportamento do RabbitMQ:
      http://tryrabbitmq.com/

    Routing key:
      É uma key especifica que relaciona a exchange com uma fila, ou seja,
      é um ID unico. Serve para mandar uma mensagem especificamente para uma
      fila.
  
    Exchange:
      Ela pega a mensagem que o publisher mandou, ela processa essa mensagem e
      descobre para qual fila essa mensagem vai ter que ser enviada(binding)
      Regra no rabbit, você nunca publica uma mensagem diretamente na fila.

      Tipos:
        Direct: Ela recebe uma mensagem e envia uma mensagem para uma especifica fila.
        Fanout: Ela vai mandar a mensagem para todas as filas que estão relacionadas(bind) a 
          esta exchange, pode ter 10 filas e será enviada para todas elas a mesma mensagem.
        Topic: Consegue colocar algumas regras a partir do routin key e encaminhar para
          a fila.
        Headers: Determina via header da mensagem para qual fila a mensagem será enviada(Formato menos usado).

    Queues/Filas:
      Durrability = Durable, quer dizer que se a máquina cair, assim que voltar a fila
      irá subir automáticamente. Transient, quer dizer que se a máquina cair, quando
      levantar não existirá mais, ou seja, não é gravada.
      Feature = Exibe o tipo que a fila é
      State = Idle significa parada

      Bind com Exchange = Você não publica diretamente na fila, mas sim na exchange,
      então é necessário linkar as duas. Para isso é só acessar a fila, ir até o menu binding
      e na opção "From exchange" digitar o nome da exchange que ela pertence.

    Producer:
      Produz uma mensagem para uma exchange

    Consumer:
      Consome uma mensagem direto de uma fila

    Observações:
      Ack = Acknologe, ou seja, recebi a mensagem e confirmei.
      Nack = No Acknologe, ou seja, recebi a mensagem e ela esta errada, erro ou algo do tipo.
      Reject = Rejeita a mensagem.
