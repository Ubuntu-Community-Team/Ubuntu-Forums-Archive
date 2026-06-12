---
title: "El GRUB no gestiona l'arrencada"
date: 2010-02-16
forum: Catalan Team
---

### Post by joaquimrubio on 2010-02-16
Ordinador de taula amb 3 HD,1 HD instal·lat al Ch 2 com a Master on hi ha el windows 7. Un altre HD instal·lat al Ch 2 com a slave on hi ha el windows XP i un tercer HD on hi he instal·lat el Karmic Koala 9.10.

A l'engegar el Pc vaig directe al W-7, sense que s'engegi el GRUB.

He provat de pulsar la tecla F12 i anar a la BIOS, per engegar des d'alli l'Ubuntu, pero em surt: GRUB error, GRUB rescue.

He reinstal·lat el Karmic sense èxit.

Aquest mateix ordinador funcionava perfecte amb 2 HD, un HD amb el windows XP i un altre amb l'Ubuntu Hardy Heron que després vaig substituir pel Karmic Koala fins que el S.O. em va començar a avisar del que el HD amb el winXP estava a punt d'espatllar-se definitivament i em vaig decidir a afegir un 3er HD amb el W-7.

---

### Post by bonsaiw on 2010-02-16
Hola joaquimrubio, si pel que he entès vas fer això: HD1 W-XP, HD2 KK, i després afegir el HD3 W-7, em sembla que es normal que et falli el KK perquè el grub es fa un embolic (no sé ben bé com ni perquè)
Si després vas reinstalar KK va ser amb els altres dos HD engegats? és a dir, amb els 3 HD funcionant? si és així i no et va, prova només el HD amb windows a vere si van i et deixen escollir entre el 7 i l'XP, i torna a instalar KK amb tot conectat.

Si no va, no se'm ocorre res més xD

---

### Post by joaquimrubio on 2010-02-17
Gràcies per contestar, bonsaiw.

El procés va ser: Primer, a la botiga m'instal·len un tercer HD i instal·len el Windows Xp i el Windows 7. 

Després, jo, instal·lo el Karmic Koala en el tercer HD, funcionant tots els 3 HD.

Abans d'instal·lar el KK, a l'engegar l'ordinador anava directament cap al windows 7 i no permetia escollir quin HD carregar.

Després d'instal·lar el KK, passa el mateix.

El curiós és que entrant a través de la BIOS i escollint el KK, el GRUB generi un missatge d'error. Com si hi hagués una incompatibilitat entre el GRUB i el W-7.

---

### Post by bonsaiw on 2010-02-18
Hola joaquim, he pensat que si no t'anava bé abans d'instal·lar ubuntu a lo millor al ficar ubuntu s'ha liat encara més així que he estat googlejant una mica i trobat això:

 "hay que instalar los diferentes sistemas operativos **con tan solo el disco en el que vamos a hacer la instalación conectado, debiendo tener el resto de discos duros desconectados**. Esto es aplicable también en el caso de que haya que reinstalar o reparar uno de los sistemas. 
Una vez instalado el sistema operativo correspondiente, ya podemos conectar los demás discos y elegir con cual vamos a arrancar desde el **Boot Menu** de la BIOS"

d'aquí: [http://www.configurarequipos.com/doc1056.html](http://www.configurarequipos.com/doc1056.html)

vaja, que potser no els van instal·lar bé els windows.

iii..... no sé, jo he estat un temps amb 2 hdd, un amb XP i l'altre amb linux, i tenia un ATA, i altre SATA, i per això no havia de preocupar-me per lo de "master" i "slave", pero si tu tens tots ATA CREC que hauries de posar el hdd de linux com a master, o en un cable sol.

Jo provaria això ;)

---

### Post by joaquimrubio on 2010-02-19
Gràcies, Bonsaiw.

Si ho entenc bé haig de desconnectar els 2 HD on hi ha Microsoft, després posar el 3er HD com a master i després reinstal·lar el KK.

Suposo que haig d'obrir la torre i desendollar físicament els 2 HD.

Per a posar com a master, imagino que trobaré algún tutorial al Google, i que es fa via software.

No he obert mai cap torre, serà una bona oportunitat per a començar a esbrinar com és un pc per dins. No he configurat mai cap BIOS, espero que no sigui massa complicat.

Gràcies altra vegada.

---

### Post by bonsaiw on 2010-02-21
Nooooo xD

o sí, pero això no volia dir jo xD

El que deia el link que et vaig posar era que per instal·lar windows en diferents HDD's havies de instal·lar un i després l'altre però amb només aquell disc dur posat, vaja que a lo millor a la tenda t'ho van fer malament.

Però per instal·lar qualsevol linux amb windows, has de tenir windows ja posat i a l'hora de posar linux tenir engegat també el hdd de windows.

Lo de master i slave és físic. És el "pont" de corrent que hi ha entre la conexió de corrent i la de dades de tots els hdd's ATA (és a dir, els que tenen el cable ample com 3 dits i molt prim, i gris).

El que jo intentaria al teu cas sería instal·lar tot de zero, primer un hdd amb windows, treure'l, instal·lar l'altre amb windows, posar els dos hdd's de windows i el tercer, i instal·lar KK en ell.

Això si, vigilant amb lo de master/slave. ;)

---

### Post by joaquimrubio on 2010-02-23
D'acord, ara ho entenc. No tinc els CD de Microsoft i no voldria tornar a aquesta botiga, ja pensaré que faig. 

Moltes gràcies per tot el seguiment del cas.

---

### Post by bonsaiw on 2010-02-24
De res ;)

Sort!

---

### Post by joaquimrubio on 2010-04-10
El problema finalment era com estaven montats els 3 HD en la placa base, si es posa el w-7 com a primari no funciona, sí funciona si es posa el xp o el Karmic com a primari.

---

