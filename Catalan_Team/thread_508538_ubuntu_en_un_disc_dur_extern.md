---
title: "ubuntu en un disc dur extern"
date: 2007-07-24
forum: Catalan Team
---

### Post by bratac on 2007-07-24
Bones, 

tinc un company que té el disc dur de l'ordinador ple, m'ha dit que volia comprar-se un disc dur extern i li he proposat de partir el disc nou i instal·lar-hi ubuntu. Jo això ho he fet amb mac, però no sé si es pot fer amb ubuntu, podré arrencar ubuntu si l'instal·lo al disc dur extern, pot donar algun problema? Hi ha alguns discs durs externs millors que altres?

fins ara,

---

### Post by benetj on 2007-07-25
Hola,

El que plantejes si que es pot fer, si l'ordinador, (si es modern si que ho permetrà) permet arrancada desde disc extern.

En principi no hi ha d'haver cap problema, l'única pega es si el disc (o la capsa) es USB, millor si  es Firewire per la taxa de transferència.

Esper que t'hagi ajudat.
Salut!!

---

### Post by bratac on 2007-08-21
El meu dubte és, si val la pena fer-ho en extern o intern.

Com anirà millor l'ordinador si tinc els dos sistemes en intern i la informació en extern o si tinc un sistema (windows) en intern més extern i l'ubuntu íntegrament en extern?

Gràcies.

---

### Post by CarlesOriol on 2007-08-21
Millor en intern

---

### Post by Jordi B on 2009-01-25
Pot fer una ullada a [http://www.binefa.cat/tutorials/externalDiskCat/](http://www.binefa.cat/tutorials/externalDiskCat/)
amb títol "Arrencar GNU/Linux Ubuntu 8.10, físicament i virtual, des d'un disc dur extern". Salut i llibertat !!!!

---

### Post by jerec on 2009-01-26
Ni s'et ocurreixi instal·lar el sistema amb un disk dur extern, a mes veient que les velocitats de transferencia dels USB amb Linux van de pena

De poder-se fer, es pot fer, però això son invents.
Parteix el disc dur intern i posa-hi el Linux a la partició i els fitxers a on et sobri espai o al USB extern.

---

### Post by Jordi B on 2009-01-27
Estic escrivint aquesta resposta des d'un portàtil arrencat amb un disc extern corrent una GNU/Linux Ubuntu 8.10. Ahir va estar funcionant en tres ordinadors d'escriptori diferents, un altre portàtil i el vaig arrencar, a més, des d'un GNU/Linux Debian Lenny per consultar el meu correu electrònic. La velocitat de la connexió USB 2.x és més que acceptable i si hi ha prou RAM (>= 1GB) puc virtualitzar altres sistemes operatius a una velocitat més que acceptable (de fet ni es nota). L'ordinador que ara estic emprant tan sols te 512MB i em limito a virtualitzar amb menys sistemes. Abans de dir que això són "experiments" amb un to de condescendència convido a qui vulgui que ho provi per ell/a mateix/a. Les tasques que faig habitualment són la programació en C i C++, sobre GTK2.0 i Qt4 (fins i tot fent servir el nou IDE QtCreator 0.9.1), tinc un servidor apache i ftp per fer intercanvi d'arxius amb els meus alumnes, faig servir el programa de disseny electrònic KiCad, les eines d'oficina Open Office i tinc un client de correu electrònic (Thunderbird) amb més de 7GB en correus acumulats en diferents comptes. A més tinc connexió de xarxa inalàmbrica preconfigurada per a més de 7 punts d'accés diferents. Hi porto treballant d'aquesta manera des de finals de novembre del 2008. Problemes?. Els mateixos que amb un disc dur intern. Que em dona?. La llibertat de connectar-me a qualsevol ordinador que pugui arrencar un disc dur extern (gairebé tots amb menys de quatre anys d'antiguitat). Us convido a que ho proveu, ho tasteu i després opineu el que creieu més adient. Salut i llibertat !!!!

---

### Post by Miquel Ubuntero on 2009-01-27
Hola comapnays.
Si serveix d'informació, estic d'acord amb el Jordi. Jo també estic escrivint aquest text des de un Ubuntu 8.10 amb un disc extern connexió usb i va de conya. Només tinc 512 MB de ram, però no és cap problema fins hi tot per fer correr VirtualBox de manera aceptable.
Salut i molt programari lliure! amb H.D. intern o extern ;)

---

### Post by jerec on 2009-01-27
No es que vulgui "consentir-li" o no que instal·li el SO en un disc dur extern.
La configuració que fas servir tu no em diràs que es un escenari normal, apart en el especial cas que expliques d'anar-lo arrencant en diferents maquines per fer docencia, de fet al ubuntu 8.10 ja donen opcions de crear un "USB Startup disk" (amb algun bug encara) i sinó també tenim els Live-CD amb totes les seves limitacions de volatilitat de les configuracions. I creu que ho tinc mes que provat!

El que planteja en bratac es que te un company amb el disc dur ple i necessita espai.

Per el que he entès jo el que demana es la millor opció, no si es pot fer o no (cosa que ja sabem que si).

Després de veure com funcionen els USB amb els últims kernels, el meu consell es que la millor opció es amb intern. 
Has provat de copiar algun fitxer gros amb USB (200MB a 1GB) i no te res a veure amb el mode en que esta muntat Sync o async ?¿¿

Per cert, et falten els <CR><LF>

---

### Post by Jordi B on 2009-01-28
Evidentment que si és vol fer córrer una GNU/Linux Ubuntu a un ordinador d'escriptori o portàtil de manera permanent, i única, el més adient és fer servir un disc intern. Fer-se una instal·lació a un disc dur extern ens permet treballar amb diferents màquines i amb diferents maquinaris amb un sistema operatiu adaptat a les teves necessitats. És un concepte diferent. En definitiva, no ser esclau d'una màquina en concret per poder consultar el teu correu amb un client com el Thundrbird, sinó poder-ho consultar arreu mantenint l'històric de correus i tenir tot aquell programari i personalització sempre a mà.

El gran avantatge que hi veig a l'hora de fer-se una instal·lació a un disc extern és que el públic fins ara reticent a GNU/Linux el pot començar a fer servir. Com? :
- Fent córrer sobre el mateix ordinador que funciona amb algun sistema operatiu privatiu una configuració acabada. No el CD/DVD d'arrencada amb programari bàsic o una memòria USB limitada per ensenyar feines reals.
- No sé si heu patit el particionat d'un ordinador amb finestres vista fent-ho amb GParted per encabir un GNU/Linux?. Si no tens certa idea "avançadeta" de com fer-ho deixes no funcional el finestres vista. I el que era reticent a GNU/Linux el deixes més reticent encara. Si per l'individuu en particular és tan important aquell sistema operatiu, pot fer servir plenament una GNU/Linux amb llur màquina.
- Hi ha certs programes, per exemple els de dibuix 2D, on el programari lliure no té un acabat igual de professional (estic pensant en el QCad i l'AutoCAD). A mi, tot sovint, em diuen : "Ja faria servir el GNU/Linux però necessito l'AutoCAD". Instal·les una màquina virtual amb el VirtualBox amb el sistema operatiu privatiu finestres xp amb l'AutoCAD instal·lat i ja tenim un nou usuari que fa servir clients de correu electrònic, navegadors i eines d'oficina sobre GNU/Linux. Em pots dir que amb el wine també ho pots fer. Sí i amb un disc intern o extern és igual de fabulós (però has de saber configurar correctament les dlls al wine. No és trivial.)
- Els usuaris de programari exclusiu per finestres (ara estic pensant en programadors de xips) poden dur llur configuració arreu mitjançant un finestres virtualitzat. Amb GNU/Linux ho poden fer i amb el seu finestres no. Això potser entra en contradicció amb els puristes del programari lliure. Jo sóc del parer que quan més usuaris GNU/Linux fem, més fàcil i més acceptació tindran els postulats del programari lliure i compartit en el futur. Com tot, és discutible. Però quant més usuaris de GNU/Linux existeixin millor per tots. 

En quant a perquè prefereixo el disc dur extern a la memòria USB (que és molt fàcil de fer amb la GNU/Linux Ubuntu 8.10) o al DVD?

En quant a l'escenari normal de feina es tenir configurats tots els programes que et calen per a poder treballar amb normalitat.

A [http://www.binefa.cat/tutorials/externalDiskCat/](http://www.binefa.cat/tutorials/externalDiskCat/) s'explicita :

*El problema de les memòries USB és que llur tecnologia assegura, “només”, un milió de cicles d'escriptura i l'espai per desar informació és limitat (per exemple si es té pensat executar diferents màquines virtuals o desar arxius grans). Els discs durs de butxaca permeten, avui en dia, ser una alternativa seriosa de portabilitat.*

Si n'has fet servir sabràs que una partició de l'USB duu una imatge iso i després tenim uns arxius de persistència havent de treballar sobre /tmp per desar feina real (el monitor del sistema sempre marca una ocupació del 100% de la partició de feina). Quan et demana fer actualitzacions has d'anar en cura de no actualitzar el kernel. Si sense voler ho fas, intenta introduir-ho a l'espai no canviable i alenteix qualsevol instal·lació de programari nou. És un experiment molt interessant però no aporta normalitat de feina. 

En quant al disc CD/DVD arrencable pots fàcilment fer-t'ho amb remastersys ([http://www.binefa.cat/tutorials/remastersys/](http://www.binefa.cat/tutorials/remastersys/)). Però al ser un dispositiu mecànic es nota una diferència de velocitat important, i a més has de fer servir algun disc intern o extern per desar la feina que vas desenvolupant.

Això del disc extern és una alternativa real de feina (evidentment depèn de quina) i és una possibilitat més que molta gent no coneix. A més aconseguim més usuaris al món GNU/Linux.

Salut i llibertat !

---

