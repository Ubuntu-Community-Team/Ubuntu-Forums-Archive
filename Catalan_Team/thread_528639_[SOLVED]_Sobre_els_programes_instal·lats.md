---
title: "[SOLVED] Sobre els programes instal·lats"
date: 2007-08-18
forum: Catalan Team
---

### Post by Usuari on 2007-08-18
Hola familia,

per les preguntes ja veureu que sóc novell en això del Linux. M'he instal·lat l'Ubuntu en una partició del disc i he estat consultat documentació, però és tant extensa, que per trobar algunes coses em torno boig; a veure si vosaltres que sou experts em podeu contestar quatre preguntes:
- és normal que trigui més en iniciar-se l'Ubuntu que el Window$? Es queda bastant temps amb el 'checking file systems'...?
- es pot iniciar el sistema sense que em munti tots els discos? Em munta particions de Window$ que no necessito i crec que això també fa perdre temps a l'inici...?
- hi ha algun lloc on surti una llista dels paquets que tinc instal·lats i que no forma part del programari original de Ubuntu? (És a dir, coses que he instal·lat manualment o amb el Synaptic que no venien en el disc de Ubuntu); En cas contrari, us anoteu el que aneu instal·lat per si mai heu de reinstal·lar tot el sistema?
- Vosaltres instal·leu (o teniu instal·lats) paquets que no estan mantinguts per Ubuntu? Suposa algun risc en quant a seguretat del sistema?

Per avui això és tot, perdoneu si faig preguntes tontes... per alguna cosa hem de començar els novells!!

Salut!

---

### Post by CarlesOriol on 2007-08-18
pufffff...

Usuari sempre és millor que facis les preguntes d'una en una... segur que tindras més respostes. La veritat és que quan llegeixes una pregunta així de llarga costa de respondre. 

Au anem per feina:

> trigui més en iniciar-se l'Ubuntu que el Window$? 
Tot depen del que tinguis installat. Quan comences a carregar-los cap dels dos és ràpid iniciant. Jo no m'hi preocuparia gens excepte si el temps fos enorme. Pots trobar algun modul que et ralenteixi l'engegada (ndiswrapper n'és un).

> es pot iniciar el sistema sense que em munti tots els discos?
Edita el /etc/fstab i posa un # davant dels discs que no vols que munti.

> una llista dels paquets que tinc instal·lats
dpkg --get-selections > instala.txt.
En cas de desastre pots reinstallar tota la llista carregant-la amb el synaptic.

> instal·leu (o teniu instal·lats) paquets que no estan mantinguts per Ubuntu
Entenc que vols dir per ubuntu i la comunitat, ja que tot i que els paquets mantinguts per ubuntu son un munt la suma important la fan aquests més els repositoris universe.

Jo et recomanaria que no installesis programari d'altres fonts fins que estiguis més segur en el sistema. Et pots trobar evidentment problemes de seguretat (malware etc..) i problemes de restriccions (programes no lliures com el googleearth o l'skype).

Si no tens cap altre solució pots fer-ho però cerca sempre l'equivalent lliure. Per això no usem windows o mac, no?

---

### Post by Usuari on 2007-08-18
Gràcies Carles,

això és velocitat! :)

---

