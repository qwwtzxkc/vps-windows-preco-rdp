# VPS Windows barato: preço real, tamanho certo para RDP e o que a renovação esconde (com os planos da AvaHost e do mercado brasileiro)

Um VPS Windows barato no Brasil começa em **R$ 16,90/mês** na DokeHost e em **R$ 39,90/mês** na HostMF, considerando o valor de entrada que cada empresa publica no próprio site. A distância entre esses dois números vem de três lugares: a licença do Windows, a taxa de instalação e o tempo que a promoção dura. Abaixo eu abro esses três itens, mostro a faixa de preço da AvaHost para Windows e indico qual configuração faz sentido para RDP, ERP, SQL Server e automação.

> **Resumo rápido:** para uma instância única, com RDP e um software só, a linha Windows gerenciada da AvaHost começa em **€5,00/mês** (1 vCPU, 2 GB de RAM, 25 GB NVMe). Para SQL Server, ERP ou vários usuários conectados ao mesmo tempo, o topo documentado é **€40,00/mês** (8 vCPU, 16 GB, 160 GB NVMe).
> 👉 [ver os planos Windows da AvaHost e o preço em euro](https://my.ava.hosting/aff.php?aff=15562)

## Os planos Windows da AvaHost, com o que está documentado

A AvaHost trabalha com duas linhas para Windows: o VPS Windows comum, com KVM e RDP disponível logo após o deploy, e o VPS Windows gerenciado, em que a equipe da empresa cuida de provisionamento, configuração do sistema, instalação de software, aplicação de patches e upgrades. A faixa de preço publicada vai de €5,00 a €40,00 por mês, e os dois extremos têm configuração fechada:

| Plano | vCPU / RAM | Armazenamento | Preço | Contratação |
| --- | --- | --- | --- | --- |
| Entrada (Windows gerenciado) | 1 vCPU / 2 GB | 25 GB NVMe | **€5,00/mês** | [contratar](https://my.ava.hosting/aff.php?aff=15562) |
| Topo (Windows gerenciado) | 8 vCPU / 16 GB | 160 GB NVMe | **€40,00/mês** | [contratar](https://my.ava.hosting/aff.php?aff=15562) |

Entre esses dois pontos existem configurações intermediárias, e a linha Windows não gerenciada tem tabela própria. Vale abrir a página de preços e conferir o tier exato antes de fechar, porque a diferença de alguns euros muda bastante o que cabe dentro da máquina.

O que acompanha os planos, segundo a documentação da própria AvaHost:

- **KVM com partição rígida** de vCPU, teto de RAM garantido e NVMe isolado, sem vizinho de host disputando I/O.
- **IPv4 dedicada** em todos os tiers.
- **RDP disponível imediatamente** após o provisionamento, sem camada de compatibilidade.
- Suporte a **Docker e Windows Containers**, a ferramentas de configuration management (Ansible, Chef, Puppet) e a agentes de monitoramento como Windows Exporter e Datadog Agent.
- Na linha gerenciada, **administração completa incluída** no valor mensal.

A cobrança é em euro. Para quem compara em real, o valor final depende do câmbio do dia e das taxas da forma de pagamento escolhida, então a conta de cabeça sempre fecha um pouco acima da etiqueta.

## De onde vem a diferença entre R$ 16,90 e R$ 39,90

Os dois preços brasileiros são de planos diferentes, não de uma mesma configuração com markup distinto. A DokeHost anuncia VPS a partir de R$ 16,90/mês e trabalha com uma escada visível: R$ 20,90 no plano de 1 GB, R$ 55,90 no de 2 GB, R$ 79,90 no de 4 GB e R$ 103,90 no de 8 GB. A HostMF parte de R$ 39,90/mês com SSD NVMe, tráfego ilimitado, Anti-DDoS, Windows ou Linux, ativação imediata e garantia de 7 dias.

Quem compara só o número de entrada está comparando o plano mais baixo de uma com o plano mais baixo da outra, sem olhar o que está dentro. Um VPS de R$ 39,90 em 12 meses custa R$ 478,80. O plano de 2 GB da DokeHost, a R$ 55,90, custa R$ 670,80 no mesmo período. A pergunta útil é qual dessas máquinas roda o seu software sem travar no meio do expediente, e isso depende de RAM e disco, não do valor da vitrine.

SLA também não se compara no vácuo. A HostMF anuncia 98,9% de uptime, a DokeHost cita 99,6% apenas para a linha VPS Trader e a Contabo fala em 99,9% do site inteiro. São recortes diferentes, medidos em escopos diferentes.

## O que encarece um VPS Windows barato

**A licença do Windows é cobrada por núcleo.** A Piensa Solutions é o exemplo mais transparente: Windows Server 2022 ou 2025 custa **+5 €/vCPU** sobre o preço base. Numa máquina de 4 vCPU, são 20 €/mês só de licença, o que pode dobrar a fatura de um plano pequeno. Quando dois provedores oferecem 4 vCPU com diferença de 15 €/mês, a explicação costuma estar aí, e não na qualidade do hardware.

**A taxa de instalação fica fora do anúncio.** A STRATO cobra **9 € de Einrichtung** por servidor, um valor único que não aparece no "x €/Mon." da vitrine. Em contrato de um mês, são 45% a mais no VPS M de 20 €.

**"A partir de" costuma ter prazo.** A Contabo vende o CLOUD VPS 4 (4 vCPU, 8 GB, 100 GB SSD) por €5,50/mês, mas o preço está limitado aos **primeiros 24 meses**; o valor depois disso não está claro na página e vale pedir por escrito. A STRATO trabalha com duas promoções paralelas no mesmo servidor: 13 € no primeiro mês e 20 € depois, ou 13 € nos três primeiros meses e 20 € do quarto em diante. No VPS M, a segunda opção dá 3×13 + 9×20 = **219 € no primeiro ano**, contra 240 € de quem paga cheio desde o início. A partir do 13º mês, são 240 € por ano em qualquer um dos casos.

**Backup raramente está incluso.** A STRATO escreve explicitamente que os backups não fazem parte do pacote. A HostMF lista backup automático como opcional. Se o seu ERP roda nessa máquina, some o custo do backup antes de comparar com o concorrente que já inclui.

## Qual configuração comprar para cada uso

Não existe número oficial de sessões RDP por GB, e qualquer tabela que prometa isso está chutando. O que dá para usar como régua são as configurações que os próprios provedores vendem como degraus:

**2 GB (entrada):** um software só, uma sessão RDP por vez, uso de escritório remoto. O Windows Server sozinho já ocupa parte relevante dessa RAM antes de qualquer aplicação abrir, então é o tier para quem tem uma tarefa única e previsível.

**4 GB:** a STRATO posiciona o VPS M exatamente aqui, com 2 vCores e 120 GB NVMe por 20 €/mês. Serve para uma aplicação com banco local pequeno ou duas sessões simultâneas leves.

**8 GB:** é o ponto em que SQL Server e ERP passam a respirar. A Contabo coloca 8 GB no CLOUD VPS 4, a AvaHost topa em 16 GB e a STRATO vende 8 GB no VPS L por 40 €/mês. Para banco de dados, o ganho não é só de RAM: a própria AvaHost argumenta que o NVMe isolado reduz a latência de fsync do transaction log e evita picos de iowait causados por vizinhos.

**16 GB ou mais:** múltiplos sites, containers Docker, várias sessões RDP ao mesmo tempo ou um banco com volume real de escrita. É o tier em que o custo por GB começa a cair e a diferença entre provedores fica menos relevante do que a estabilidade do I/O.

## Onde fica o servidor e o que isso muda no RDP

A AvaHost opera a partir de um data center próprio em Chișinău, na Moldávia, com infraestrutura endurecida, canal de aproximadamente 50 Gbit/s e capacidade alta de mitigação DDoS, segundo uma análise independente publicada em 2026. Isso define para quem o serviço serve.

Para automação, bots, tarefas agendadas, hospedagem de aplicação interna e qualquer coisa que rode 24 horas sem ninguém olhando a tela, a distância física é irrelevante. Para RDP interativo pesado, com edição gráfica, terminal de trading ou digitação em sistema que responde a cada tecla, um servidor em São Paulo entrega uma experiência melhor do que um na Europa Oriental. A latência maior aparece no dia a dia, não no anúncio.

A mesma análise independente cita pagamento em cripto e suporte 24/7 com opções gerenciadas. Um relato de cliente registrado nela menciona uptime decente e demora na resposta de tickets, com variação de velocidade de carregamento entre momentos. Vale ler os relatos antes de colocar produção crítica ali.

## Seis verificações antes de pagar

**1. A versão do Windows está inclusa no preço?** A Piensa cobra +5 €/vCPU pela licença; outras casas embutem no valor. A AvaHost não publica a lista de versões na documentação de produto, então confirme por ticket qual build vem instalado e se a licença está no mensal.

👉 [tirar essa dúvida direto com a AvaHost antes de contratar](https://my.ava.hosting/aff.php?aff=15562)

**2. Backup está incluso ou é add-on?** Na STRATO não está; na HostMF é opcional. Pergunte a frequência, o prazo de retenção e quanto custa restaurar.

**3. O RDP está aberto para a internet inteira?** A Piensa entrega o template Windows com a porta **3389 liberada para qualquer origem** e recomenda restringir. A Contabo orienta limitar o RDP a IPs confiáveis ou usar VPN. Se o painel não permitir essa restrição, troque a porta e coloque firewall na própria máquina.

**4. Qual é o prazo de reembolso?** A HostMF anuncia 7 dias de garantia. A ficha técnica independente da AvaHost registra **30 dias** de money-back guarantee. É o tipo de informação que muda a decisão quando você está testando um software que pode não rodar.

👉 [conferir os planos e a garantia da AvaHost](https://my.ava.hosting/aff.php?aff=15562)

**5. Emitem NF-e e aceitam Pix ou boleto?** A DokeHost emite NF-e. A HostMF aceita Pix, cartão e boleto, sem contrato de fidelidade. Para PJ brasileira, nota fiscal não é detalhe contábil, é requisito. Com a AvaHost, a cobrança é em euro, o que já muda o fluxo de pagamento.

**6. Reinstalar é grátis e apaga tudo?** HostMF e DokeHost permitem reinstalação ilimitada e gratuita pelo painel; a DokeHost aceita ISO personalizada. A Piensa oferece console KVM para o mesmo fim. Em todos os casos, reinstalar zera o disco. Tenha snapshot ou backup antes.

## Perguntas frequentes

**Por que VPS Windows é mais caro que Linux?**
Porque a licença é cobrada à parte e, em alguns provedores, por núcleo. A Piensa Solutions precifica Windows Server 2022 e 2025 em +5 €/vCPU. Um plano Linux de 4 vCPU e o mesmo plano com Windows podem diferir em 20 €/mês só por isso.

**4 GB rodam Windows Server com folga?**
Rodam o sistema e uma aplicação leve. A STRATO vende 4 GB como degrau de entrada da linha Windows, com 2 vCores. Para SQL Server com base real, 8 GB é o piso mais seguro.

**Preciso comprar backup separado?**
Na maioria dos casos, sim. A STRATO declara que backups não estão incluídos e a HostMF trata o recurso como opcional. Backup não é item de economia: é o que decide se um disco corrompido custa uma hora ou uma semana de trabalho.

**A promoção expira e o preço sobe quanto?**
Depende do formato. A Contabo segura €5,50 por 24 meses. A STRATO cobra 13 € no primeiro mês ou nos três primeiros e volta para 20 € depois, o que dá 219 € no primeiro ano contra 240 € a partir do segundo. Antes de assinar, pergunte qual é o valor de renovação e por quanto tempo ele vale.

**VPS gerenciado vale a pena para quem só quer RDP?**
Se você mesmo instala o software e aplica atualização do Windows, a linha não gerenciada resolve. A gerenciada da AvaHost faz sentido quando ninguém do time quer administrar patches e configuração de sistema, e o custo mensal passa a incluir esse trabalho.

## Como decidir

Faça a conta por uso, não por preço de vitrine.

Se você precisa de uma instância única, um software, uma sessão RDP por vez e não liga para latência, o tier de entrada de 2 GB resolve, e a faixa de €5,00/mês da AvaHost cabe nesse cenário. Se entra SQL Server, ERP ou mais de uma pessoa conectada ao mesmo tempo, comece em 8 GB. Se o ambiente tem containers, vários sites ou banco com escrita constante, vá para 16 GB e olhe o tipo de disco antes do número de vCPU.

Duas confirmações antes de digitar o cartão: a versão do Windows e a licença estão dentro do preço, e existe backup com retenção definida. O resto é ajuste fino.

👉 [abrir a página de planos Windows da AvaHost](https://my.ava.hosting/aff.php?aff=15562)
