---
title: "Sense so amb Ubuntu 9.10"
date: 2009-10-29
forum: Catalan Team
---

### Post by carevolta on 2009-10-29
Hola, amigues i amics. Vaig actualitzar el cap de setmana a Karmic Koala (ja ho sé, massa prompte, però era quan tenia temps lliure) i tot ha eixit de meravella, excepte que m'he quedat sense so, tan sols els dels sistema com el pip en encendre la màquina (ja ho sé, massa prompte per queixar-me).
El cas és que mai havia tingut aquest inconvenient i sóc un ignorants absolut en targes de so, en si és millor ALSA o Pulseaudio, etc. En fi, no tinc excessiva pressa, però he trobat algunes referències a la xarxa de errades semblants i voldria confirmar que no sóc l'únic, i saber si teniu alguna pista sobre què pot ocórrer.
Gràcies i endavant!

---

### Post by SiscoGarcia on 2009-10-29
carevolta, jo també sóc bastant ignorant en targes de so i així, però tinc clar que sense informació és difícil que algú et puga ajudar. Hauries de dir quina màquina tens, quina tarja d'àudio, i tota la informació que puga ajudar.

Mentrestant, si no ho has fet, pots anar googlejant amb aquestes dades ;)

---

### Post by carevolta on 2009-10-29
Tens tota la raó, Sisco. Segons m'informa Sysinfo:
Tinc un processador AMD Sempron(tm) 2600+ (o siga, bastant rudimentari)
I respecte del so:
Silicon Integrated Systems AC'97 Sound Controller
Subsystem: AS Rock Incorporation Device 7012
El cas és que si vaig des de l'icona de so a preferències-maquinari, la casella està en blanc, així que no puc seleccionar quin dispositiu vull configurar. El controlador de volum de Pulseaudio, diu que tinc un dispositiu de sortida fingida. Al mesclador ALSA de Gnome quan li demane que em mostre les propietats de la targeta de so, es queda pensant o bé peta, com en la imatge que adjuntava abans. I Default sound card (des de sistema-preferències) es queda pensant també i no obre res.
Intuisc que durant la instal·lació no ha detectat la targeta de so, però res més. Ja he googlejat, a ubuntu-es, per exemple, hi ha diverses consultes, però o són massa específiques o no conclueixen res. I en anglés també s'hi troba alguna informació, però tampoc hi veig clar.
La qüestió és que a ma casa em puc entretenir, però tots els aparells de l'associació són idèntics, així que no puc/dec actualitzar de moment, per por que ocórrega el mateix. Ja dic, no és res greu, però si un poc molest trobar-se amb aquests inconvenient. En fi, gràcies, amic Sisco, i paciència.

---

### Post by orestesmas on 2009-10-30
Sembla un problema del PulseAudio, un invent que no m'acaba de convèncer.

Sona molt bèstia, però mira de desinstal·lar tots els paquets relacionats amb el pulseaudio, de manera que el sistema usi l'ALSA original.

Pensa que sempre pots tornar a instal·lar els paquets esborrats.

No sé com és de fàcil fer-ho en una Ubuntu amb Gnome, perquè em penso que el PulseAudio està més imbrincat en el sistema. En KDE no ho està tant i esborrar el PulseAudio m'ha estalviat molt problemes amb les aplicacions.

---

### Post by bikerbaixcamp on 2009-11-11
Bones! Ja tinc la Ubuntu 9.10 i prou bé! :p

Això si, hi ha un problema i no és en el meu ordinador (que de moment va bé). A l'ordinador de la meva companya (que és un ordinador d'aquests d'escriptori compactes) tampoc no li funciona el so. 
El fet es que al meu ordinador vaig instal·lar la 9.10 a partir del cd; al seu ordinador a partir d'una actualització des del gestor d'actualitzacions; tot i que això potser tampoc no té massa importància com a informació ja que són ordinadors diferents. Però bé, al que anàvem. 
Ah, i també li passa que amb un kernel se li queda penjat a l'entrada de l'escriptori i no va i s'ha d'utilitzar l'altra kernel; però bé.. seguim.

Doncs com molt bé diu en "carevolta" també li passa això a l'ordinador. No et deixa seleccionar res. Ah, com a informació dir que la ubuntu 9.10 al cd live si que funcionava el so; és a dir, que no funciona quan està instal·lat i amb la 9.04 (que és la que venia instal·lada) si que anava el so. 
És un ordinador nou, el seu, i per això potser no detecta la targeta de so... però la veritat que no en tinc ni idea..

Salut! Salut!

---

### Post by sordoman on 2009-11-12
Hola Carevolta.

Bé,  pel teu escrit suposo que amb la versió 9.04 si que tenies sò.

A partir d'aqui el primer que probaria es a synaptic, hi ha el següent paquet
```

linux-backports-modules-alsa-karmic-generic

```un ocellet em diu que poster et funciona, si no fós aixís reinstala el paquet

```

alsa-firmware-loaders

```i si tampoc funciona probes el següent

```
[INDENT]sudo aptitude install module-assistant build-essential
 sudo module-assistant prepare,update
 sudo aptitude install alsa-source
 sudo module-assistant build,install alsa
 sudo depmod 
 [/INDENT]
```ja explicaràs a veure com va

Per cert jo diria que no es un problema del Pulseaudio, tot i que encara esta una mica verd, el problema bé més de Alsa, pulseaudio "recull" els sòns del sistema i els envia a l'Alsa, si alsa no reconeix el HW malament rai

Molta sort

---

### Post by bikerbaixcamp on 2009-11-12
Sordoman, jo ho he provat.

Bé, he provat fins al segon pas i res. El tercer de moment no l'intento que és tard i demà tinc moltes coses a fer.

No tenia instal·lat cap dels dos paquets; i els he instal·lat. Però la cosa segueix igual, tampoc m'apareix per configur el so, i també em surt lo de la sortida fingida.

Ah, com a cosa "curiosa" tan ara com abans d'instal·lar els paquets, a estones a estones no, es veu que amb l'Amarok puc escoltar la música però molt fluixeta i amb els altaveus (bonets) posats al màxim. Se sent, però molt fluixet. Alguna explicació per aquest fenomen paranormal? xD

Bé, ja us dic, tardaré alguns dies a provar el tercer pas, però de moment res.

Sort!

---

### Post by papapep on 2009-11-13
Crida l'alsamixer des d'un terminal:

```
alsamixer
```

i comprova que tens tots els controls importants ben amunt, i cap en posició "mute" (MM).

---

### Post by carevolta on 2009-11-13
Oops, no sabia com explicar ací que ja havia solucionat l'incovenient i que, en aparença, no tenia res a veure amb els paquets relacionats amb el so, perquè vaig provar gairebé tot el que indiqueu. Tanmateix encara ignore perquè ha ocorregut el que explique tot seguit. El cas és que vaig notificar un bug i em van respondre amb les següents instruccions (que el mestre Cubells, a qui també vaig consultar, donà per bones):
Em responien més o menys això:

"Sembla que després d'actualitzar al Karmic encara esteu arrancant amb un
nucli no-Karmic. Hi pot haver hagut un problema durant l'actualització del grub"
I em suggerien aquests passos:
"Please try:
 sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
 sudo update-grub
 sudo reboot

After rebooting run:
 uname -a

Verify that the kernel you are now booting is of the
2.6.31 variety"

Senzill i eficaç!

---

### Post by sordoman on 2009-11-13
Genial que estigui solucionat!!

Hi ha molta gent que els hi ha passat, tot just reiniciar no carrega en nucli nou si no l'antic, uf quin merder!! i si no mireu pels altres forums#-o

Solucions sensilles a problemes grosossos \\:D/

Fins la propera):P

---

### Post by ifanlo on 2009-11-14
Jo vaig patir el mateix problema... i precisament aquest matí, m'he trobat en que ja funcionava el so.

Això de la versió del nucli ho havia comprovat, i el uname -a em deia que carregava el nucli actual 2.6.31-14 però a les propietats del so no identificava dispositiu.

No m'amoïna gaire, total pel que s'ha de sentir!   :)

Però el cas es que aquest matí, ja ha sonat la cosa... i m'identifica un "Analog Stereo Duplex", sigui això el que sigui... tinc un portàtil Compaq nc6320, amb el so integrat; crec que hauria de dir no-se-que de Intel, però bé... com deia en bikerbaixcamp, fenòmens paranormals.

:D

Salut,

---

### Post by bikerbaixcamp on 2009-11-19
Bones!

Ho tinc "semi-solucionat". La solució la té en carevolta!

Ara bé, jo tinc un problema afegit. 

Si carrego 2.6.31-14 se'm queda la pantalla (i tot) congelada al cap de 10 o 15 segons de carregar-se, això si el so funciona. Però per tant, no puc utilitzar-lo. 

PD: Ara si que funciona!!!!! Després d'entrar diversos cops, ha funciona. Coses paranormals....

Doncs el que deia es que si entrava al 2.6.28... funcionava bé, però sense so. Era allò del nucli no-karmic. 


Bé, res més... que sembla que ja estigui arreglat!

Salut i molt bona feina ubuntaire!

---

