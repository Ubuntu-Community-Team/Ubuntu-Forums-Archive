---
title: "No puc cambiar la mida de la partició."
date: 2011-06-19
forum: Catalan Team
---

### Post by Frealof on 2011-06-19
Bon dia,

L'altre dia em vaig decidir a passar d'Ubuntu Intrepid Ibex (que ja no està mantingut) a Natty Narwhal. La idea era desar les diferents carpetes d'usuari del directori /home a un disc dur extern, però com que no m'hi cabia tot vaig pensar que podria reduïr la partició que tenia, que ocupava tot el disc alliberant així prou espai per poder instalar els dos sistemes. fins aquí tot bé. Per fer-ho, vaig utilitzar GParted des d'una live que vaig fer mitjançant Startup Disk Creator. 

Un cop instalats els dos sistemes vaig passar les dades de /home d'una partició a l'altra sense problemes. Un cop fet això em vaig decidir a eliminar la partició on hi tenia l'Intrepid Ibex mitjançant altre cop GParted.

Ara el què volia fer és "restaurar" el tamany de la partició /dev/sda1/ utilitzant el l'espai lliure que em queda... Desmunto les particions i, no sé per què no puc, ni moure-la, ni aumentar-la... Amb la swap /dev/sda5/ si que puc, però amb l'altre, no. 

He adjuntat un parell d'imatges per mostrar les particions.

A algú se li acud alguna idea?

---

### Post by quitus on 2011-06-19
En les captures que mostres, no es veuen els punts de muntatge. Seria interessant poder veure-ho.

Tens la swap en la mateixa partició que vols eliminar, i a mes a mes posa extended que crec que vol dir lògica, en comptes de ser primaria, crec que seria el més adient (si m'equivoco si us plau corregiu-me) 

Jo eliminaria tota la partició "extended" i tornaria a crear la partició per la memòria swap, això vol dir editar l'arxiu fstab però no crec que sigui gaire problemàtic.

Et quedarà una partició lliure que pots fer servir per separar la carpeta "home" de la partició on tens la instal·lació, ja que veig que l'opció d'actualitzar la distribució no et fa el pes.

salut

---

### Post by wgarcia on 2011-06-19
No es recomanable saltar-se versions, excepte quan s'actualitza d'una LTS a la següent (per exemple quan surti la 12.04 a l'abril de l'any que ve, es podria actualitzar la 10.04 directament  la 12.04). 

Però si es vol actualitzar de la 10.04 a la 11.04 primer seria recomanable fer la actualització 10.04 -> 10.10 i després 10.10 -> 11.04.

---

### Post by Frealof on 2011-06-20
Hola, 

Com puc saber els punts de muntatge de les particions? Suposo que et refereixes a què us pengi la sortida que em doni entrant alguna ordre al terminal...

La Swap, partició d'intercanvi, està a /dev/sda2 ja és una partició diferent, i no la vull eliminar,ja que em sembla que vaig llegir a alguna banda que és necessària.

La partició que voldria ampliar és /dev/sda1/ on hi tinc instal·lada l'ubuntu 11.04, on vaig fer instal·lació neta i actualitzada cada quan surten actualitzacions. Com es veu a les imatges que he penjat em queden unes quantes gigues sense formatar, en teoria, i sóc conscient que per desconeixement potser fico la pota, hauria de poder ampliar la partició /dev/sda1 sense problemes... però sembla que la teoria em falla i no en sé la causa... 

Gràcies de totes maneres ;)

---

### Post by wgarcia on 2011-06-20
Per poder ampliar la partició l'espai sense assignar ha d'estar contigu a la partició. Per tant si vols incrementar la /dev/sda1 has d'anar incrementant les altres particions per absorbir l'espai posterior, i després tornar-les a reduir deixant espai lliure endavant de la partició, per anar movent aquest espai buit fins que quedi contigu a la /dev/sda1, no sé si m'explico...

Com sempre és fonamental tenir còpia de tot perquè, no hauria de passar, però remoure les particions és una operació força radical i si hi ha algun problema al disc pot produir-se una pèrdua de dades.

---

### Post by quitus on 2011-06-20
La partició sda5 es a dins de sda2, per aquesta raó no pots eliminar l'espai sda2 sense eliminar sda5.

---

### Post by orestesmas on 2011-06-20
> **wgarcia said:**
> Per poder ampliar la partició l'espai sense assignar ha d'estar contigu a la partició...

A no ser que facis servir el sistema LVM, que et permet anar afegint fragments de disc buits ubicats aleatòriament a un sol "volum lògic"

---

### Post by Frealof on 2011-08-25
Ja està fet, després de passar dades amunt i avall per tenir-les segures em vaig decidir a provar el què wgarcia va proposar, i, fa funcionar, gràcies..

---

