---
title: "Primeres impresions amb la 9.10"
date: 2009-11-17
forum: Catalan Team
---

### Post by lluisalguero on 2009-11-17
Hola ubuntaires,

doncs després de un mal regust de boca amb versions anteriors d'Ubuntu. Avui m'he baixat la 9.10 i l'he instal·lat. Dir-vos (i això ho faig extensiu a tot aquell que entra a buscar informació) que l'instal·lació ha estat perfecta. Tenia una mica de por a l'hora de fer les particions (el meu portàtil venia amb el vista preinstal·lat), però els missatges son molt i molt clars de tot allò que s'ha de fer.

Avui m'ha funcionat a la primera el ratolí, el so i la tarja de video...estic molt satisfet. Només m'he liat una mica a l'hora de configurar les IP's i DNS per a la connexió a la xarxa, però me n'he sortit.

Ara el deixarem tal i com m'agrada...i esperar no ficar molts de missatges demanan ajuda.

Una salutació,
Lluís

---

### Post by MiquelBLL on 2009-11-17
Doncs a mi fatal, inclus em fa pensar si seguir o no amb ubnutu, la 9.04 si em va anar força be pero ara tot a canviat.
Vaig convertir de ext3 a ext4 sense formatejar i en principi va sortir be. Al actualitzar a la 9.10 un mun de problemes que no vaig saber com solucionar, sort d´un amic que hi entent i que m´ho va arreglar, resulta que els que vam convertir de ext3 a ext4 al actualitzar no reconeixia les particions, es veu que es tenia que tornar a reinstal.lar el grup, aixo una, l´altra es que no es va instal.lar els linux-headers crec i no carregaba els drivers de la grafica nvidia que tinc, jo no ho hauria pogut arreglar mai es cosa d´experts, tambe m´ho va poguer arreglar, i ara gaire be no puc utilitzar el firefox va molt lent sobretot al comensament i dels videos flash res de res no sén veu cap o van a salts. Tinc instal.lat el swiftfox els swiftweasel epiphany en cap es veuen els videos de per exemple youtube o tu.tv, amb l´opera en funcionaben pero ja eb una actualitzacio de la 9.04 van deixar de funcionar els videos, no se pensaba que en aquets dies ja hauria  sortit alguna actualitzacio pero segueix igual. Per altra bsanda si no comnecto a internet sembla que vagi mes o meins igual que amb el 9.04, pero no he nott res especial, el temps d´inici es el mateix mes o meyns, a ara em funciona el mediacenter moovida que amb el 9.04 no funcionaba. Per algunes paines es comenta que el firefox ara no funciona gens be.

---

### Post by Rubunter on 2009-11-17
has pensat en formatar i reinstal·lar?

---

### Post by jdk9 on 2009-11-17
> **MiquelBLL said:**
> Doncs a mi fatal, inclus em fa pensar si seguir o no amb ubnutu, la 9.04 si em va anar força be pero ara tot a canviat.
Vaig convertir de ext3 a ext4 sense formatejar i en principi va sortir be. Al actualitzar a la 9.10 un mun de problemes que no vaig saber com solucionar, sort d´un amic que hi entent i que m´ho va arreglar, resulta que els que vam convertir de ext3 a ext4 al actualitzar no reconeixia les particions, es veu que es tenia que tornar a reinstal.lar el grup, aixo una, l´altra es que no es va instal.lar els linux-headers crec i no carregaba els drivers de la grafica nvidia que tinc, jo no ho hauria pogut arreglar mai es cosa d´experts, tambe m´ho va poguer arreglar, i ara gaire be no puc utilitzar el firefox va molt lent sobretot al comensament i dels videos flash res de res no sén veu cap o van a salts. Tinc instal.lat el swiftfox els swiftweasel epiphany en cap es veuen els videos de per exemple youtube o tu.tv, amb l´opera en funcionaben pero ja eb una actualitzacio de la 9.04 van deixar de funcionar els videos, no se pensaba que en aquets dies ja hauria  sortit alguna actualitzacio pero segueix igual. Per altra bsanda si no comnecto a internet sembla que vagi mes o meins igual que amb el 9.04, pero no he nott res especial, el temps d´inici es el mateix mes o meyns, a ara em funciona el mediacenter moovida que amb el 9.04 no funcionaba. Per algunes paines es comenta que el firefox ara no funciona gens be.

Dic el mateix que l'anterior, perquè no formatejes?

I pel que fa el Flash, instal·lat el paquet gnash, va bastant bé ;)

I si no t'agrada el firefox, proba el chromium

---

### Post by lluisalguero on 2009-11-17
De moment l'unic problema que tinc (creuem els dits), és amb una aplicació que tinc a la meva web i que ve directament de les dades que puja de la meva estació meteorològica

El problema és el Microsoft Silverlight ([http://www.meteotortosa.cat/web2/index.php?option=com_wrapper&view=wrapper&Itemid=148](http://www.meteotortosa.cat/web2/index.php?option=com_wrapper&view=wrapper&Itemid=148)).

Miraré si trobo alguna informació al respecte

---

### Post by lluisalguero on 2009-11-17
Ara remenant pels menus i configuracions, veig que al portàtil algú se li ha menjat 1 Gb de RAM :confused:

això és el que em tira el "top"

top - 01:20:46 up  1:48,  2 users,  load average: 0.02, 0.05, 0.01
Tasks: 174 total,   3 running, 170 sleeping,   0 stopped,   1 zombie
Cpu(s): 22.3%us,  2.4%sy,  0.0%ni, 75.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
[COLOR="Red"]Mem:   3094484k total[/COLOR],   970184k used,  2124300k free,    48200k buffers
Swap:  7293468k total,        0k used,  7293468k free,   516392k cached

Quant realment el meu portàtil té 4 Gb de RAM (amb els Vista així m'ho indicaba). Això no crec que sigui massa normal, o potser si...ves a saber

---

### Post by xxibeca on 2009-11-18
El que dius de les 4-3G de ram em sembla que és un problema de versió de 32 ó 64 bits, si has instal·lat la de 32 només reconeix fins a 3G.

---

### Post by lluisalguero on 2009-11-18
> **xxibeca said:**
> El que dius de les 4-3G de ram em sembla que és un problema de versió de 32 ó 64 bits, si has instal·lat la de 32 només reconeix fins a 3G.

Doncs quina collonada !!

---

### Post by papapep on 2009-11-18
> Doncs quina collonada !!

No és ben bé això. Són limitacions d'adreçament de memòria. :)

Abans es podia evitar això instal·lant el nucli de la versió servidor que porta el [PAE]("http://es.wikipedia.org/wiki/Extensi%C3%B3n_de_direcci%C3%B3n_f%C3%ADsica"), però ara no es pot.
A canvi, per saltar-t'ho, pots instal·lar un nucli que sembla que han preparat els desenvolupadors específicament per aquests casos:

```
sudo apt-get install linux-generic-pae
```

No sé si té efectes secundaris, en principi no tindria per què, però no conec ningú que el faci servir.

---

### Post by MiquelBLL on 2009-11-18
Ja vaig estar a a punt de formatejar tot i que perdrie configuracions correues pop i programes pero no se perque tinc que formatejar per instal.lar una nova versio, aixo no passa ni en windows ni en mac ni en altres linux em sembla. El sistema em va be, l´unic que no funciona son els navegadors, lo de posar el gnash ja el tenia posat, he esborrat el flash i deixat nomes el gnash pero tampoc. I ja te dic hi ha molta gent que te problemes amb el firefox, a mes jo tinc problemes amb tots els navegadors. Suposo esperare alguna actualitzacio, i ja et dic no es nomes que no funcionin els videos si no que noto que cuan esta l´ordinador conectat a internet no va fi del tot de vegades, per exemple noto al mourer una finestra que no va lo fina que te que anar, va com a saltets, en fi, que sembla com si amb la nova versio nessesites una maquina molt mes potenta, a que em sona aixo? Tinc AMD Turion 64 a 2G i nvidia GF 6100. I res que amb el Virtualbox, xp i firefox els videos es poden mirar.

---

### Post by papapep on 2009-11-18
M'hi jugaria dos pèsols a que tot té a veure amb el controlador de la gràfica. No em demanis gaire més, que de gràfiques no controlo, però tots els símptomes hi apunten.

---

### Post by MiquelBLL on 2009-11-18
Vaige toquetejan sembla que lo dels videos s´arreglat mes o meyns..... he nat a preferencies/aplicacions i on esta lo de Flash video estaba avans posat en ´utilitza VLC per defecte´ ara he posat en ´Demana-ho sempre´ i ara els videos funcionen, tambe he toquetejat lo dels pluguins al Opera i selecionat lo correcte i ara tambe en funcionen el videos al Opera, i tambe a Swiftweasel, Swiftfox i tambe amb Epiphany, jo flipo, nomes he tocat lo de las preferencies i he habia esborrat el gnash, o sigui ara nomes tinc lo del Flash palyer instal.alt no se si tornar a instal.lar el gnash.

---

### Post by papapep on 2009-11-18
Les referències que tinc del Gnash no són gens bones. A gairebé tothom li porta problemes. També va molt combinat amb el controlador de la gràfica, o sigui que és complicat de saber a vegades què fa què.
En tot cas, és un bon projecte d'extensió flash lliure, però li falta camí encara.
I el que sí que no has de fer és tenir dues extensions Flash instal·lades.

---

### Post by MiquelBLL on 2009-11-18
Si es veritat, al tornar a posar el gnash llavors tornaven a fallar els videos, no es poden tenir els 2 instal.lats. Lo de las preferencies que habia tocat no te res a veurer i he tornat a posar a Flash  lo del vLC per defecte. Gracies. Tot i aixi el firefox va mes lent, a vegades tarda en reacionar per exemple al voler canviar de pestanya.

---

### Post by Daerun on 2009-11-18
Jo no he tingut problemes seriosos (a part del tema de les ttf-mscorefonts que he obert :P ). Al principi el Firefox anava molt lent, però vaig aplicar un truquet que vaig llegir a [SOMGNU](http://www.somgnu.cat/2009/11/17/firefox-mes-rapid-a-gnulinux/) i ara va com la seda.

Com a problemes petits, doncs coses més vanals, com per exemple que instal·lant el joc d'icones Hydroxygen resulta que algunes icones no s'apliquen (el menú Sistema no mostra les icones, tot i que els seus submenús sí).

---

### Post by PatrickVogeli on 2009-11-18
Doncs jo la veritat es que n'estic molt content. Amb el meu Acer 1810TZ funciona tot de maravella, va rapid i cuida la bateria.. es fantàstic.

Salut

---

### Post by SiscoGarcia on 2009-11-18
Jo també n'estic, de content. De fet no m'estranya ja que he estat provant-lo des que era alpha1 i ja llavors reconeixia força bé el maquinari; d'alguna manera ara l'ubuntu ha assolit un nivell que permet tenir les versions inestables al nivell de les estables de fa uns 2 anys.

Entenc que els problemes que encara apareixen a cada canvi de versió entren dins del que podríem anomenar raonable, i a més en poc temps es resolen.

---

