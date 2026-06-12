---
title: "Reflexió: Ubuntu Maverick sembla que no suportarà màquines antigues"
date: 2010-06-08
forum: Catalan Team
---

### Post by giorgiograppa on 2010-06-08
Ens recorda en Papapep la notícia que la propera versió d'Ubuntu, Maverick, està previst que [no suporti màquines antigues]("http://www.webupd8.org/2010/06/ubuntu-1010-maverick-meerkat-wont-run.html") sigui compilada per a màquines tipus i685 i posteriors.

La decisió, que es justifica amb la intenció d'aprofitar millor les característiques del maquinari modern, deixarà fora de la família Ubuntu màquines més antigues (no tinc clar a quins models es refereix exactament, ho sento: algú ens ho pot aclarir?). A més, sembla que està afectant a [models actuals]("https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/587186"), però que segueixen esquemes anteriors.

Tenint en compte que un dels valors a destacar dels sistemes GNU/Linux és la possibilitat d'allargar la vida del maquinari, fa l'efecte que Canonical, guiada per interessos mercantils (totalment legítims, és clar), s'està allunyant del model clàssic del programari lliure. Per exemple, Lubuntu seria una mostra de fidelitat a aquell esperit clàssic (i una contradicció a aquesta proposta "modernitzadora").


Us semblaria bé obrir una reflexió sobre aquest tema en aquest fil?

Com ens pot afectar, a nivell personal?
Com ens pot afectar, a nivell de comunitat?
Hi podem fer alguna cosa, personalment o com a grup?

Tema filosòfic, doncs.

---

### Post by SiscoGarcia on 2010-06-08
Hola Giorgio,

No sé com quedarà, però he obert una idea al brainstorm d'ubuntu amb aquesta queixa: [http://brainstorm.ubuntu.com/idea/25085/]("http://brainstorm.ubuntu.com/idea/25085/")

És el que se m'ha acudit fer a nivell personal i que podeu recolzar com a comunitat... també podem discutir-ho i prendre alguna altra decisió.

EDITO:

[[IMG]http://brainstorm.ubuntu.com/idea/25085/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/25085/)

---

### Post by papapep on 2010-06-08
Moltíssimes gràcies, nois. He escampat el tema del Brainstorm a l'identi.ca: [http://identi.ca/notice/35373987](http://identi.ca/notice/35373987)

A veure si serveix d'alguna cosa...

---

### Post by giorgiograppa on 2010-06-08
Per manca de canals de comunicació, no serà!

Algú em pot aclarir això de "i686" a què es tradueix? Pentium III, Pentium II, Pentium a-seques-pobrissó-meu... És que no me n'he sortit a interpretar la Wiquipedia en "inglix".

Entenc que el 586 es correspondria amb el Pentium a-seques-pobrissó-meu, que el 686 seria un Pentium II (i equivalents), i, per tant, aquest marcaria el nivell més baix de compatibilitat "màquina-Maverick": m'erro de molt?

---

### Post by wgarcia on 2010-06-08
Això és el que he trobat:

8086 = 8-bit
80186 = 8-bit
80286 = 16-bit
80386 = 32-bit
80486 = 32-bit
80586 = 32-bit = Pentium, Pentium MMX, K5, K6, K6-II, K6-III
80686 = 32-bit = Pentium Pro, Pentium II, Pentium III, Athlon, Athlon XP, Opteron*, Athlon FX-51*, Athlon FX-53*, Athlon 64*
80786 = 32-bit = Pentium 4

* = 32-bit/64-bit

per tant sembla que els que quedarien fora serien els primers Pentium a seques i Pentium MMX.

Sí és veritat que alguns ordinadors recents de baix consum venen amb arquitectura 80586, suposo que alguns miniordinadors, però no sé quins.

---

### Post by AlexMuntada on 2010-06-08
Teniu l'especificació corresponent al launchpad:

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-686-compile](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-686-compile)

No està pas gaire ben argumentada (sobretot si la comparo amb d'altres que he vist de l'equip d'ubuntu-server), si més no ni l'especificació ni el wiki corresponent no estan al dia.

Veureu que hi ha un bug relacionat, el mateix que comentàveu abans. Una manera de fer-se notar és indicant que el bug us afecta personalment (per exemple, el paio que el va obrir desenvolupa solucions de terminals lleugers basades en LTSP d'ubuntu).

A títol personal, puc simpatitzar més o menys amb el problema però no m'afecta directament. Jo ja vaig patir aquest *reciclatge* amb l'arquitectura powerpc i amb l'sparc fa temps. En el primer cas, la comunitat d'ubuntu segueix mantenint un port per a powerpc perquè molts desenvolupadors tenen equips Mac antics. En el segon, vaig acabar migrant a Debian.

---

### Post by Diegstroyer on 2010-06-08
Fa temps que cada cop em costa més instal·lar les noves versions d'ubuntu en portàtils i equips vell, en alguns casos ha estat del tot impossible.

Sempre ens quedaran distribucions que no deixaran de donar suport a Pc's antics.

Ho trobo poc encertat, encara que comprensible, això em recorda a ATI i els seus "legacy"... des de aleshores no he recomanat ATI mai més, espero que no hagi de fer el mateix amb ubutnu.

Salutacions.

---

### Post by PatrickVogeli on 2010-06-08
Doncs jo trobo que en algun moment s'ha de dir prou... de la llista del wgarcia, l'AMD K6-III és la maquina més nova que es queda fora... i te 10 anys. Realment hi ha algu funcionant amb una ubuntu estandard amb un PC de fa 10 anys?

A més, per a donar-li una volta més, l'AMD k6-III és molt minoritari en comparació amb el Pentium 3, que seguiria sent compatible, per tant, és un problema que afecta, numericament, a una part marginal dels usuaris d'ubuntu.

Així que.. en algun moment s'ha de tirar endavant i seguir avançant, no es pot estar mirant constantment pel retrovisor.

Salut

---

### Post by giorgiograppa on 2010-06-08
Gràcies per l'aclariment, wgarcia! Veig que no anava del tot desencaminat.

Em sorprèn, però, que dins de les màquines "ubuntariables" encara estarien els Pentium Pro i els Pentium II: creieu que encara queden moltes d'aquestes en funcionament? Vull dir, en un ambient empresarial, de producció, i no en mans dels estudiosos de la matèria.


Pel que fa als Pentium III, no tinc cap dubte de la seva vigència, almenys en el terreny domèstic (no us avorriré parlant-vos d'Acopdegarròtix, el meu servicial servidor, amb Fluxbox inclòs). Ara bé, quina empresa els mantindria en ús? Sí, potser com a servidors; però no hi tinc informació directa; tret, és clar, que en el meu institut estan jubilant-los a la carrera, però és més perquè l'empresa de manteniment s'ha negat a donar-los suport tècnic (i treballen amb Windows, a més a més...).


Suposo que els més afectats seran aquests ordinadors lleugers de nova creació on no es podria instal·lar la següent versió d'Ubuntu. Però, com apunten l'Àlex Muntada i Diegstroyer, els queda la solució de migrar a una altra distro: per sort, l'ecosistema GNU/Linux, amb unes tres-centes distribucions en actiu, encara ens dóna moltes opcions on triar (i no tot ha de ser Ubuntu). Fins i tot, encara podrien sortir guanyant si migressin a sistemes especialitzats en aquest tipus de màquina, com ara projectes del tipus Moblin o MeeGo (en desconec els detalls tècnics, igual estic clavant la pota).



Trobo, doncs, que d'entre tota aquesta varietat, algunes distribucions (més d'una en cada cas, si-us-plau!) s'haurien d'especialitzar en uns tipus de màquina, i d'altres, en altres tipus; i, és clar, també seria bona cosa comptar amb unes quantes distribucions "totterreny". El que no seria convenient per a la comunitat, crec, seria esperar que totes les distribucions fossin "totterreny"; de fet, seria tan dolent com que totes s'especialitzessin en el mateix conjunt de màquines.

(Estic aplicant a la informàtica els principis sobre la bondat de la biodiversitat: no sé si és correcte, però no he vist demostrat enlloc que siguin casos tan diferents com per no permetre aquest paral·lelisme.)



El que està clar, crec, és que la Canonical treu diners del mercat empresarial (bé, ho suposo, ho espero); que aquest mercat, en general, no manté en funcionament màquines de l'estil del 80486 (i, si ho fan, dubto que estiguin en condicions de contractar res amb la Canonical); i, per ser competitius, Canonical ha d'oferir el millor producte possible, aquell que millor aprofiti els recursos de les màquines amb què treballen els seus clients. De pas, crec que també ens oferirà un millor producte a la major part dels usuaris domèstics.


Crec que hauríem de veure la qüestió filosòfica (i no dic "filosòfica" amb valor pejoratiu, sinó tot el contrari: els que m'heu vist fer la presentació del PL en les festes ubuntaires ja sabeu que ho valoro molt i ho subratllo molt) de l'aprofitament de les màquines antigues com una cosa que depèn de l'ecosistema GNU/Linux en el seu conjunt, i no esperar o desitjar que sigui Ubuntu qui salvi totes les màquines.



De manera que, després de meditar-hi una mica (i després, sobretot, d'haver llegit els comentaris dels companys), ja no ho veig tan greu com al principi. Seguirem el fil, però.

---

### Post by SiscoGarcia on 2010-06-08
Patrick i Giorgio, puc entendre el que voleu dir, però crec que Canonical demostraria més que pensa en els humans... en tots els humans, si continués mantenint la compatibilitat de la nova versió per màquines velles. No fent això està condemnant sobre tot a qui té menys recursos (i d'aquests a Sud Àfrica n'hi ha molts) a migrar cap a altres distros o a mantenir-se en la versió actual. Això, des del meu punt de vista, és discriminatori per part de qui vol abanderar la defensa d'[una sèrie de valors]("http://www.ubuntu.com/project/about-ubuntu/our-philosophy") (concretament que el programari hauria de ser lliure i accessible per tothom).

---

### Post by papapep on 2010-06-08
Un dels efectes negatius més importants que veig fins ara, és que tot el projecte LTSP (Linux Terminal Server Project) queda tocat i exclòs d'emprar Ubuntu, ja que, precisament, es fonamenta en reaprofitar dinosaures microinformàtics o equips amb processadors de baix rendiment, com el Geode LX700, que si no l'erro és una versió de baix consum amb les instruccions d'un i586 per a dispositius encastats.
I, fins i tot, em preocupa més el fet d'aquests girs *sense previ avís* que fa Canonical, que una decisió en concret (tot i que greu des del meu punt de vista). Direu que ho pot fer, que és una empresa, etc. És cert, però jo també hi puc estar en desacord i fer el que cregui adient :)
Fa temps, molt, que em preocupa que Ubuntu estigui acaparant tants recursos de la comunitat. No som tanta la gent activa pel programari lliure, i, dels que conec, l'immensa majoria estem dedicats a Ubuntu, no excloem res, però no tenim temps per altra cosa. Això em fa plantejar-me si hauria de ser més agnòstic i no lligar-me tant a una empresa/distribució en concret (sí, ja sé que tenim [Caliu]("http://caliu.cat/"), per sort :D)
Respecte el que diu el Giorgio, ho trobo prou encertat. I això només fa que reforçar, sota el meu punt de vista, encara més el meu pensament de que no es poden posar tots els ous al mateix cistell i menys quan no en tens gaires (ara comporteu-vos i no aprofiteu el tema per on no toca :P).

---

### Post by giorgiograppa on 2010-06-09
> **SiscoGarcia said:**
> ... però crec que Canonical demostraria més que pensa en els humans... en tots els humans, si continués mantenint la compatibilitat de la nova versió per màquines velles.

Sí, Sisco: significaria que l'esperit "ubuntu" és quelcom més que un simpàtic eslògan publicitari. Però crec que haurem de ser una mica més realistes i admetre que Canonical no és ca Debian. Que, per cert, continua essent un exemple de distribució multiplataforma i encara suporta màquines antigues, oi?, i suficientment sòlida per no fer pensar en la seva desaparició en qüestió de mesos.

Pel que fa als efectes sobre els usuaris de màquines molt velles... No estem oblidant que acaben de treure una LTS i que els desktop tenen garantit el suport per tres anys, i els servidors per cinc? Vols dir que, dins de tres anys, no s'hauran caigut de velles aquestes pobres (i heroiques) màquines, xip a xip?

I, d'altra banda, creus que, ara per ara, Ubuntu és la millor opció per a maquinari tan limitat? Lubuntu, sobre un Pentium III, em funciona bé, però no m'he atrevit a instal·lar-lo sobre un Pentium II (que encara estaria suportat).

Aprofito per llençar una altra pregunta (amb intencions pràctiques de cara a aquesta reflexió): quina és la màquina més antiga o més poc potent sobre la que heu instal·lat un Ubuntu amb entorn gràfic? Ni que sigui emprant una Alternate, és clar.


Els més perjudicats, com apunta en Papapep i s'ha comentat en el fil, serien, probablement, aquelles noves màquines d'inspiració antiga. Però sempre els quedarà l'opció de migrar, o de fer un port d'Ubuntu pel seu compte (no sé si és fàcil o difícil; bé, fàcil, fàcil, no serà, per descomptat).

---

### Post by giorgiograppa on 2010-06-09
> **papapep said:**
> Un dels efectes negatius més importants que veig fins ara, és que tot el projecte LTSP (Linux Terminal Server Project) queda tocat i exclòs d'emprar Ubuntu, ja que, precisament, es fonamenta en reaprofitar dinosaures microinformàtics o equips amb processadors de baix rendiment, com el Geode LX700, que si no l'erro és una versió de baix consum amb les instruccions d'un i586 per a dispositius encastats.

Sí; no en conec els detalls tècnics, però semblen els més perjudicats. Com he dit a l'altre apunt, els resultaria molt difícil migrar o fer un port d'Ubuntu?

> **papapep said:**
> I, fins i tot, em preocupa més el fet d'aquests girs *sense previ avís* que fa Canonical, que una decisió en concret (tot i que greu des del meu punt de vista). Direu que ho pot fer, que és una empresa, etc. És cert, però jo també hi puc estar en desacord i fer el que cregui adient :)

Crec que aquest és punt clau de la qüestió: la manera com Canonical pren les seves decisions. Sí, totalment lícita; però, tot i les coses positives que Ubuntu ens ha aportat (popularitat, projecció pública, facilitat d'ús per a l'usuari "del carrer"...), caldrà estar atents a aquests canvis sobtats.

> **papapep said:**
> Fa temps, molt, que em preocupa que Ubuntu estigui acaparant tants recursos de la comunitat. No som tanta la gent activa pel programari lliure, i, dels que conec, l'immensa majoria estem dedicats a Ubuntu, no excloem res, però no tenim temps per altra cosa. Això em fa plantejar-me si hauria de ser més agnòstic i no lligar-me tant a una empresa/distribució en concret (sí, ja sé que tenim [Caliu]("http://caliu.cat/"), per sort :D).

En efecte: la gent amb capacitat de fer coses (desenvolupadors) dins del programari lliure no augmenta amb la mateixa proporció que els usuaris "del carrer" (intueixo), sinó que és una xifra que es deu mantenir, si fa no fa, inalterada. I si tots es queden (us quedeu) supeditats a Ubuntu, la resta de distros, aquella infodiversitat de què parlava ahir, se'n veurà perjudicada; i això sí que seria negatiu per allò que dius dels ous i del cistell (qualsevol analista d'inversions et diria el mateix: procura no invertir tots els calés en accions de la mateixa empresa, per molt bé que sembli anar).

---

### Post by wgarcia on 2010-06-09
He estat intentant llegir sobre aquest tema, no he trobat massa més cosa que l'enllaç que va aportar el GiorgioGrappa i l'entrada al sistema d'errors Launchpad. El que no em queda clar és si les limitacions de maquinari antic venen pel nucli o per altres elements addicionals de l'actualització. Si venen pel nucli doncs tard o d'hora afectaran a totes les distribucions.

Per una altra part a l'entrada d'error que mencionava, es parla d'un error que dóna una llibreria del compilador gcc, i d'aquí surt una intervenció del que manté aquestes llibreries que diu que Maverick no suportarà processadors anteriors als i686. Però en discussions posteriors diu que les màquines "thin" per servidors, tipus Geode LX700, tot i ser i586, com són més modernes tenen pràcticament totes les optimitzacions dels i686. En el cas concret de l'error reportat es corregeix amb un canvi menor. Per tant potser el tema no és tan preocupant com sona. 

I per últim si l'optimització per i686 queda frenada per mantenir la compatibilitat amb màquines tan antigues, doncs encara hi ha una justificació addicional per trencar la compatibilitat cap a baix. De totes maneres per màquines tan antigues ja hi ha distribucions específiques per aprofitar-les al màxim, tipus Puppy Linux o així, no?

---

### Post by kiakli on 2010-06-09
Hola,
Però teoricament un equip antic podria seguir funcionant durant cinc anys més amb l´ultima LTS, no? El problema és la versionitis....

---

### Post by SiscoGarcia on 2010-06-10
ja sé que pot semblar absurd que m'auto-respongui, però acabo de mirar al [brainstorm]("http://brainstorm.ubuntu.com/idea/25085/") i comença a haver moviment en relació a la idea que vaig llançar i que cito a sota:

> **SiscoGarcia said:**
> Hola Giorgio,

No sé com quedarà, però he obert una idea al brainstorm d'ubuntu amb aquesta queixa: [http://brainstorm.ubuntu.com/idea/25085/]("http://brainstorm.ubuntu.com/idea/25085/")

És el que se m'ha acudit fer a nivell personal i que podeu recolzar com a comunitat... també podem discutir-ho i prendre alguna altra decisió.

EDITO:

[[IMG]http://brainstorm.ubuntu.com/idea/25085/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/25085/)

Ja sabeu, si hi esteu d'acord voteu-la ;)

---

### Post by giorgiograppa on 2010-06-10
> **SiscoGarcia said:**
> ja sé que pot semblar absurd que m'auto-respongui, però acabo de mirar al [brainstorm]("http://brainstorm.ubuntu.com/idea/25085/") i comença a haver moviment en relació a la idea que vaig llançar i que cito a sota:

No em sembla gens absurd, Sisco: per la meva part, fa dos dies no tenia ni idea que existís el brainstorm d'Ubuntu, i suposo que no sóc l'únic que no coneix tots els canals de comunicació disponibles :-)

---

### Post by giorgiograppa on 2010-06-10
Un comentari més: he observat, a partir de l'explicació d'en wgarcia, que els 686 representen el punt on apareixen les màquines de 64 bits, i no sé si això implicarà alguna diferència important respecte a la generació immediatament anterior, la dels 586; potser aquestes diferències compliquen el fet de mantenir un branca de sistemes Ubuntu-64 i una altra, Ubuntu-32.

O potser volien tallar per algun punt i aquesta qüestió és totalment irrellevant, vés a saber.

---

### Post by SiscoGarcia on 2010-06-10
> **giorgiograppa said:**
> No em sembla gens absurd, Sisco: per la meva part, fa dos dies no tenia ni idea que existís el brainstorm d'Ubuntu, i suposo que no sóc l'únic que no coneix tots els canals de comunicació disponibles :-)

Amb absurd em referia al fet que em citava a mi mateix. Ara bé, si ha servit per donar a conèixer el tema del brainstorm ja està bé... l'ideal seria que a més la gent hi votés i féssim reflexionar als de can canonical.

Per cert, jo encara no havia votat, ho acabo de fer (pensava que no podia o que aniria implícit, però acabo de provar-ho i m'ha deixat votar).

---

### Post by kukat on 2010-06-11
> Lubuntu, sobre un Pentium III, 


Jo el tinc sobre un AMD Athlon K75 500 Mhz i **121 MB** de RAM!!!

(segons el system benchmark o com es diga el programari que ve a Lubuntu!)

I porta el Chromium com a navegador per defecte que va de meravella!!!

---

### Post by PatrickVogeli on 2010-06-11
jo també he votat, pero ho he fet en contra..

---

### Post by giorgiograppa on 2010-06-11
> **kukat said:**
> Jo el tinc sobre un AMD Athlon K75 500 Mhz i **121 MB** de RAM!!!

Lubuntu hauria estat la gran meravella si hagués esdevingut sabor oficial en aquesta fornada.

---

### Post by davidsol on 2010-06-12
Bona tarda gent!
com a tècnic he de dir que per la supervivència de linux a l'escriptori i servidor vs la resta de sistemes operatius necessita rendiment, estabilitat i estar adaptat al maquinari sobre el que correrà en major nombre, l'actual. Per tant, per una millor efectivitat i rendiment és millor eliminar les màquines antigues i compilar pel processadors d'un nivell mínim "acceptable". Fins aquí d'acord amb la proposta ubuntu.

Entenc el de l'us en màquines antigues per paisos amb pocs recursos, però crec que és millor tenir una versió per això ja que sino penalitza la resta i si no s'utilitza on més recursos hi han acabarà sent un projecte no viable, ja que els pròpis usuaris no l'utilitzaran.

Malauradament crec que una cosa no casa amb l'altra com seria desitjable i l'alternativa de una versió a part no està malament.

---

### Post by kimet on 2010-06-12
Ubuntu es una distribució suportada per una companyia privada, amb les 
directrius d'una companyia privada, per tant farà el que li sigui mes rendible, no hi ha volta de full.
 
 Però no s'ha de confondre ubuntu amb el total de distribucions basades en GNU amb Linux o inclús amb altres nuclis.
Hi ha moltes distribucions que corren molt bé en ordinadors antics o amb pocs recursos.

Salut.

---

### Post by SiscoGarcia on 2010-06-14
Hola,

Crec que hores d'ara ja està tot dit, tant aquí al fòrum com al [brainstorm]("http://brainstorm.ubuntu.com/idea/25085/"). No sé si és contradictori respecte al que he estat dient, però pel que heu anat aportant sembla clar que per l'usuari occidental mitjà no és un gran destorb, no tinc clar que no ho sigui pels usuaris «en vies de desenvolupament» (que no són pocs) ni pels usuaris de LTSP, i aquests són sacrificats per Canonical. Crec que podrien continuar donant-los suport, no sé quant esforç els pot suposar, però hauria estat un detall :(

Per la meua part ho deixo aquí, espero que la discussió hagi servit per reflexionar una mica sobre tot plegat... no ho sé, és probable que ens haguem precipitat en treure conclusions, ho sento si us he fet perdre el temps.

---

### Post by Daerun on 2010-06-15
No crec que hagi sigut una pèrdua de temps Sisco, encara que no hagi comentat res m'ha semblat bastant interessant tot el que s'ha dit, y personalment no sóc capaç de decantar-me per cap de les dues opcions, perqué veig avantatges i inconvenients a totes dues.

---

### Post by SiscoGarcia on 2010-06-16
> **Daerun said:**
> No crec que hagi sigut una pèrdua de temps Sisco, encara que no hagi comentat res m'ha semblat bastant interessant tot el que s'ha dit, y personalment no sóc capaç de decantar-me per cap de les dues opcions, perqué veig avantatges i inconvenients a totes dues.

Gràcies pel teu comentari Daerun, hores d'ara jo també tinc dubtes, per això vaig fer el comentari anterior.

---

### Post by CarlesOriol on 2010-06-18
Que fort!!!

No sabia que l'ubuntu encara funciones amb ordenadors de menys de 64 bits.

---

### Post by giorgiograppa on 2010-06-18
> **SiscoGarcia said:**
> Per la meua part ho deixo aquí, espero que la discussió hagi servit per reflexionar una mica sobre tot plegat... no ho sé, és probable que ens haguem precipitat en treure conclusions, ho sento si us he fet perdre el temps.

Reflexionar no és mai perdre el temps, Sisco, i crec que aquest fil ha estat molt profitós i aclaridor. Opinem el que opinem, ara ho podem fer amb més coneixement de causa :-) .

---

### Post by SiscoGarcia on 2010-06-19
> **giorgiograppa said:**
> Reflexionar no és mai perdre el temps, [...]

Per suposat Giorgio, no em referia a això...

> **giorgiograppa said:**
> [...] i crec que aquest fil ha estat molt profitós i aclaridor. Opinem el que opinem, ara ho podem fer amb més coneixement de causa :-) .

És cert que ho ha estat, però em sembla que ens hem precipitat a l'hora de «defensar» les màquines velles i hem activat uns quants fronts que si ens haguéssim informat abans potser no hagués calgut.

Tot i això, és ben cert que ara mateix n'estem més formats en aquest aspecte ;)

---

### Post by Daerun on 2010-06-22
> **CarlesOriol said:**
> Que fort!!!

No sabia que l'ubuntu encara funciones amb ordenadors de menys de 64 bits.


I inclús amb menys d'1 GB de RAM! :mrgreen:

---

