---
title: "[SOLVED] Amule no em connecta a cap servidor"
date: 2007-06-27
forum: Catalan Team
---

### Post by xoldy on 2007-06-27
Hola bona nit, estic mirant de configurar l'amule, per fer la meva alegria completa.
No he tocat cap opció de l'amule, i no hi ha manera que em connecti a cap dels servidors que amb el güin d'ous (m'ha agradat el nom) em connectava l'emule.
Tinc els ports 50068 TCP i 50069 UDP configurats i oberts per l'adreça IP de connexió.

No se m'acut per on pot venir l'error.
Alguna idea? porto unes quantes cerques al google i no trobo solucions que em convencin.
Moltes gràcies per endavant

---

### Post by papapep on 2007-06-27
Si, com dius, no has tocat res de la configuració per defecte de l'Amule, els ports que utilitza son el 4662 TCP i el 4672 UDP.
Si no és això, hauries de verificar que no tens el Firestarter capant-te els ports.

---

### Post by xoldy on 2007-06-28
Hola Papapep, el Firestarter actua per defecte si no l'has instal·lat?
La veritat es que si que el vaig instal·lar, i si que vaig tocar una cosa, vaig canviar aquests ports per defecte perquè volia aprofitar la mateixa configuració d'obertura de ports que tenia en windows.

ara li faig una ullada al firestarter.

Tot un món!

---

### Post by papapep on 2007-06-29
A veure si ho entenc:

Al router tens oberts els ports 50068 TCP i 50069 UDP per què amb l'anterior SO ho tenies així.

I al AMule no li has dit que utilitzi aquests ports? O si??

---

### Post by CarlesOriol on 2007-06-29
Ves al butó de  xarxes.

Escrius a:

IP: Port: 62.241.53.16
: 4242

Prems al butó Afegeix... i connecta.

---

### Post by xoldy on 2007-07-07
Hola a tots dos. La situació del Amule és:
- Al instal·lar l'Amule vaig posar-li com a port tcp el 50068 i 50069 amb udp. Aquests son els ports que tinc oberts al router i en windous no hi ha problema quan faig el test de ports que porta el propi emule.
- Tal i com ha suggerit en CarlesOriol, he afagit el servidor DonkeyServer N2, i efectivament se m'ha connectat, i no s'ha desconnectat (com feia amb altres servidors).
- Quan vaig a la pàgina: [http://www.amule.org/testport.php]("http://www.amule.org/testport.php") i provo de fer el test al port 50068, em diu: ***"Error: TCP port 50068 is unavailable. Make sure your firewall or router is allowing/forwarding this TCP service port and your ED2K client is running (i.e. aMule, eMule)."***
Les preguntes que se'm plantegen son:
- Si tinc ben configurat el router, perquè ja ho estava bé per windous, llavors sembla que el problema pugui venir del firewall. És possible que el firewall vingui instal·lat per defecte? Com he de fer per deixar passar aquests ports?
Moltes gràcies
Per la resta estic bastant al·lucinat amb l'Ubuntu!!!

---

### Post by CarlesOriol on 2007-07-08
Evidentment estaves funcionane en windows en mode enmascarat i amb el rendiment reduit.

Comprova el manual del teu router ja que és clar que tens els ports tancats o apuntant a una ip nula. Assegura't que la ip on reenvies sigui la que configures a la màquina i si pot ser configura-la manualment sense dhcp.

---

### Post by xoldy on 2007-07-19
Hola Carles i Papapep, finalment el tema ha quedat solucionat, obrint un altre port en el router. He obert el 50001 pel TCP i el 50010 pel udp. He fet el test desde la pàgina d'amule testport, i diu que funciona correctament. De fet ara em connecta a qualsevol servidor i baixa a una velocitat més que raonable.
Moltes gràcies a tots dos. De vegades t'entestes a seguir coses que funcionen en windows i no pares a pensar que això és un altre món.

Ara estic barallant-me per poder connectar a la xpv de la meva feina, però no consegueixo configurar correctament les dades en el kvpn. Tinc baixat el client de Cisco, però no se instal·lar-lo. em podeu ajudar amb això. He llegit el tutorial del papapep en el seu bloc, però no me'n surto. el client l'he baixat per softonic, i el tinc descomprimit a l'escriptori en una carpeta que posa vpnclient.

Un altre cop MOLTES GRÀCIES PER AJUDAR-NOS A TIRAR ENDAVANT AMB LINUX

---

### Post by papapep on 2007-07-19
> Ara estic barallant-me per poder connectar a la xpv de la meva feina, però no consegueixo configurar correctament les dades en el kvpn. Tinc baixat el client de Cisco, però no se instal·lar-lo. em podeu ajudar amb això. He llegit el tutorial del papapep en el seu bloc, però no me'n surto. el client l'he baixat per softonic, i el tinc descomprimit a l'escriptori en una carpeta que posa vpnclient.

Per això hauries d'obrir un altre fil de conversa diferent d'aquest, sinó quedaran barrejats els conceptes i és un merder ;-) 

Donc aquesta consulta per resolta i tu n'obres un altre de nova, d'acord?

---

