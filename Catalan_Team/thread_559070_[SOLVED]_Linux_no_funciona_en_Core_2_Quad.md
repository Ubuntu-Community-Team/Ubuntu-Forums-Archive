---
title: "[SOLVED] Linux no funciona en Core 2 Quad"
date: 2007-09-24
forum: Catalan Team
---

### Post by blopnotdid on 2007-09-24
M'he instalat l'ubuntu 64 bits en un core 2 quad i funciona correcte menys la conexio a la xarxa, he probat la versio de 32 bits com em van dir pero es penja directamen del cd darrencada, tot i aixo de tant de probar-ho le pogut arrencar un parell de cops i des del cd anava be i la conexio tambe, pero a la que linstalava ja no arrencava i es quedava penjat.
Despres vaig probar el Suse, vaig instalar la versio de 64 bits tan en gnome com amb kde i un cop finalitzada linstalacio i engegava el pc es quedava penjkat, la versio de 32 bits del suse ja ni lagafa el cd.

Per ara tinc el windows XP, pero el detesto pq al cap duns mesos ja no hi ha res ke funcioni be es colen tot de programes basura per internet etc etc. malgrat que el linux costi molt mes instalar les coses (i kuan dic coses no vui di programes, k no es com el windows kenxufes un aparato i ja te lagafa automatic) pero amb aixo jam vaig espavilant.
Pro necesito ajuda pq sol no aconseguire instalarlo. a mes fa una setmana ke tinc el pc nou i el vui estrenar!!!

---

### Post by orestesmas on 2007-09-25
Podria ser un problema de maquinari no suportat. Si ens amplies la informació sobre el teu maquinari potser algú que tingui alguna cosa semblant et pot ajudar una mica més.

I una altra cosa que pots provar és el instal·lar amb el CD "alternate", que et fa una instal·lació en mode text i s'estalvia alguns problemes. A mi m'ha anat bé en alguna ocasió.

---

### Post by blopnotdid on 2007-09-25
Asrock 775 4Core1333-FullHD
INTEL CORE 2 Quad Q6600 2.40Ghz 775 + Ventilador 64Bits
DDR2 1024/800 Marca (x 2)
HD 500 GB 7200 SATA II Seagate

i la grafica ja va amb la placa base

---

### Post by blopnotdid on 2007-09-25
a m'oblidava de dir que  tb he probat la versio anterior de l'ubuntu en 64 i 32 i res. l'única que ha anat bé és l'ubuntu 7.04 a 64 bits, pero li falla la conexio (i funciona pq el cop que vaig poder entrar al cd live en 32 bits funcionava be)

---

### Post by orestesmas on 2007-09-25
No conec la teva placa. Si pots, prova alguna versió beta de la Gutsy (o espera al 20 d'octubre), perquè probablement suportarà millor el maquinari nou. Si el problema vé d'aquí, llavors potser s'arregli.

Però sospito que aquest no deu ser el problema, si dius que una Feisty t'ha funcionat bé algun cop...

---

### Post by blopnotdid on 2007-09-25
si de tots els ke probat l'unic que m'ha anat bé ha sigut l'Ubuntu 7.04 a 64 bits, pero fallava la connexio a la xarxa. Les altres distribucions, versions o la mateixa en 32 bits no arrenquen.
Bé doncs anire fent amb el windows fins a l'octubre que de fet ja és aquí practicament. Quan es el dia de sortida de la nova versio?
I la versio beta on la puc trobar?

---

### Post by papapep on 2007-09-25
Jo provaria la versió "alternate" com t'ha comentat l'Orestes.
He vist molta gent a la qual li ha solventat la papereta.

---

### Post by blopnotdid on 2007-09-25
alternate 32 bits o 64 bits?

---

### Post by papapep on 2007-09-25
Jo provaria amb 32, que és la que menys problemes t'ha de portar.

---

### Post by Ferri on 2007-09-25
També estaria bé que expliquessis una mica millor què vols dir que no et funciona la xarxa. Estàs parlant de l'accés a Internet, et connectes a un router, a una WIFI, amb una Ethernet? Sovint són problemes relativament senzills com posar bé els servidors DNS al network-manager. Si es tracta de suport al maquinari pot ser més complicat, però si et funcionava la versió live sembla que no hauria de ser res que no pugui tenir solució.
La possibilitat d'intentar la Gutsy és una bona opció, ja està força avançada i em sembla prou estable, però no oblidis que encara és una versió en fase de proves. Aquí la pots trobar: [Ubuntu Gutsy Tribe 5]("http://cdimage.ubuntu.com/releases/gutsy/tribe-5/")
La data prevista de la versió definitiva és el [18 d'octubre]("https://wiki.ubuntu.com/GutsyReleaseSchedule")

---

### Post by blopnotdid on 2007-09-25
alternate a 32 bits tambe es penja.
tinc baixada la de 64 i m'estic baixan la beta que m'heu dit

ferri sobre lu de conexio es un post que vaig obrir fa uns dies, el primer ke vaig obrir

---

### Post by papapep on 2007-09-25
Prova a posar-li el paràmetre "noapic" al principi, quan et surten les opcions d'instal·lació.

---

### Post by blopnotdid on 2007-09-27
us escric des del meu core 2 quad jejeje. he probat la versio beta del gutsy o com sa digui i em va bé ara. M'he posat la versio de 32 bits

---

### Post by albert-I on 2007-10-01
I que tal?
provaràs de posar-hi la de 64 bits?
que tal la velocitat? 
si la placa pot anar a 1333 pq hi has posat memòria de 800??
com va l'assignació de feina als processadors?
Es nota que em vull comprar un pc nou !!! :KS
Ens pots fer una mica de descripció ara que ha passat una mica de temps


> **blopnotdid said:**
> us escric des del meu core 2 quad jejeje. he probat la versio beta del gutsy o com sa digui i em va bé ara. M'he posat la versio de 32 bits

---

### Post by patrickfromspain on 2007-10-02
> **albert-I said:**
> I que tal?
provaràs de posar-hi la de 64 bits?
que tal la velocitat? 
si la placa pot anar a 1333 pq hi has posat memòria de 800??
com va l'assignació de feina als processadors?
Es nota que em vull comprar un pc nou !!! :KS
Ens pots fer una mica de descripció ara que ha passat una mica de temps

A vere, igual te puc ajudar, encara que no tingui un core 2 quad.

La diferencia de velocitat entre 64 i 32bits es bastant petita, menys en algunes tarees molt concretes com codificar audio i video, on es nota si vas cronometre en ma. A la practica.. et compliques en coses como el flash i el mozilla amb java.

En el tema de la memoria: encara que el FSB sigui de 1333 no significa que hi hagis de posar memoria 1333. De fet, la memoria 1333 es DDR-3 i s'han de fer 2 consideracions: ho soporta la placa? segurament no. Preu? Al voltant dels 200€/giga. Amb DDR-2 800 n'hi ha mes que de sobres (inclus amb 667 en tindries suficient) i a un preu "ajustat".

salut

---

### Post by CarlesOriol on 2007-10-02
> **patrickfromspain said:**
> La diferencia de velocitat entre 64 i 32bits es bastant petita, menys en algunes tarees molt concretes com codificar audio i video, on es nota si vas cronometre en ma. A la practica.. et compliques en coses como el flash i el mozilla amb java.


De fet si tenim en compte les extensions des del pentium MMX, MMX2, 3dNow, 3DNow2 SSE i SSE2 podem veure com per realitzar moltes feines de codificació de vídeo ja fa molt temps que es treballa amb "registres" de 64 bits per tant la diferència en velocitat no és tant important.

El 64 bits ofereix d'entrada un espai de direccionament de memòria molt més gran del que disposàvem fins ara, tot i que es pot dir que encara no estem amb l'aigua al coll.

Ens oferei un relax en l'us d'operadors en coma flotant pels seus equivalents en enters molt llargs. Però caldrà adaptar els programes.

Malgrat tot, la majoria de les llibreries mantenen un tipus forçat int32 o int16 (o un alies aquests)  en comptes d'un tipus indeterminat int que pot produir més problemes que avantatges. Per tant de moment de canvi ben poc.

Sobre el tema del flash, com comentava en un altre fil, al gutsy l'han arreglat perfectament... tot i que és una llàstima que aquest format propietari tingui encara segrestada una molt bona part de la nostra llibertat.

---

### Post by patrickfromspain on 2007-10-02
que ha pasat al flash en gutsy?? com ho han arreglat?

---

### Post by CarlesOriol on 2007-10-02
Han afegit una capa al firefox per insta&#320;lar plugins de 32 bits.

---

### Post by albert-I on 2007-10-02
I una altre manera de aprofitar el 64 bits, es tindre mes de 4 gigues de memòria.

---

### Post by patrickfromspain on 2007-10-02
> **CarlesOriol said:**
> Han afegit una capa al firefox per insta&#320;lar plugins de 32 bits.
nsplugginwrapper?

---

### Post by CarlesOriol on 2007-10-02
Crec que si.

En qualsevol cas ho fa tot sol. Obres el vilaweb amb el 64, et diu que no tens flash, l'insta&#320;la el mateix firefox usant el synaptic (aptget linux32+wrapper+pluggin+configurar-ho tot) i quan acaba ja funciona.  Un luxe.

---

