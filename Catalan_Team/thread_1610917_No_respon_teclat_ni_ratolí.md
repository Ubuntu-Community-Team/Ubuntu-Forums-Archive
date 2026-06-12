---
title: "No respon teclat ni ratolí"
date: 2010-11-01
forum: Catalan Team
---

### Post by pablinsfc on 2010-11-01
Bon dia!

Tinc un problema amb un portàtil. Va sorgir després d'actualitzar a la 10.10. Quan l'inicio i entro a l'ususari (entra directament, sense pantalla de login) perdo el control del PC: no funciona ni el teclat ni el ratolí. I no puc provar gaire rès perquè no hi puc interactuar. No funciona ni el touchpad ni cap ratolí via USB. Hi ha alguna manera de saber si hi va haver algun problema amb l'actualització, o d'entrar en un terminal... és que no sé com puc encarar el problema! :(

Moltes gràcies!

Pau.

---

### Post by wgarcia on 2010-11-01
Un cop que arribes a la pantalla per entrar amb el teu usuari i clau, prem Cntrl+Alt+F1 per accedir a una terminal, i fes aquí el login. 

Prova:

sudo dpkg --configure -a
sudo aptitude full-upgrade

a veure si ho arregla.

Si no ho arregla seria molt útil rebre el màxim d'informació sobre el teu model d'ordinador (marca i targeta gràfica principalment si ho saps, sinó des d'aquesta terminal es podrà esbrinar).

---

### Post by pablinsfc on 2010-11-01
Merci! Però el problema que tinc és que l'usuari de l'Ubuntu inicia directament sense passar per la pantalla de login. Puc entrar en mode terminal des del terminal del grub? Potser seria la manera. Perquè un cop trio el sistema operatiu carrega l'Ubuntu fins a l'escriptori.

L'ordinador és un:
ACER TravelMate 5720
Intel Core 2 Duo T5470
4Gb de RAM i 250GB d'HD

Mercii!

Edito: Ara estic pensat que segurament la millor opció és instal·lar la 10.10 de nou. Però no estic segur de que pugui fer-ho sense tocar el Vista que hi ha instal·lat a una altra partició. És el finestres el que es "menja" tota l'estructura del Grub oi? Reinstal·lant l'Ubuntu no tocarà res de Window$, pot ser?

---

### Post by wgarcia on 2010-11-02
També pots accedir a la consola (sense entorn gràfic) amb el mode "recovery",  triant l'opció "root - Drop to root shell prompt".

Un cop que hagis provat el que t'he dit, per provar si t'ha arreglat l'entorn gràfic pots fer:

sudo service gdm start

i t'arrencarà l'entorn gràfic.

---

### Post by pablinsfc on 2010-11-02
Bon dia. wgarcia merci per l'ajuda, però crec que no m'he explicat del tot. El terminal al que tinc accés és la línia de comandes del grub. amb una capçalera grub> he estat mirant per les comandes possibles (help) però no veig com iniciar l'ubuntu amb un kernel anterior o similar.

A les opcions del Grub només tinc "Ubuntu" i "Windows". Les altres estan "amagades" nose si les puc activar des de les opcions de commandes del grub.

El que he fet ara és intentar capturar les linies que surten quan s'inicia l'ubuntu abans de mostrar l'escriptori. En reprodueixo algunes:

[FONT="Courier New"]Boot from (hd0,4) ext3 [...]
Starting up...
mount: mounting none on /dev failed: No such device
chroot: cannot execute /etc/apparmor/initramfs: No such file or directory
init: unreadahead main process (1168) terminated with status 5[/FONT]

A partir d'aquí mostra un seguit de linies del tipus

[    19.936752]  sdhci: Secure Digital Host Controller
[    19.936800]
[             ] etc.

Estic per iniciar un Live-CD i copiar aquests directoris, però no se si ho solucionaria...

---

### Post by wgarcia on 2010-11-02
Però al grub no et surt una línia donant-te l'opció d'entrar a l'Ubuntu en mode "recovery"?

---

### Post by kimet on 2010-11-02
> mount: mounting none on /dev failed: No such device
chroot: cannot execute /etc/apparmor/initramfs: No such file or directory
init: unreadahead main process (116 terminated with status 5


Això sembla greu, intentaria entrar amb un live-cd i provar d'esbrinar alguna cosa mes, logs?, provar d'instal.lar un altre kernel des de un chroot...

Salut.

---

### Post by pablinsfc on 2010-11-02
@wgarcia: No, estan totes amagades. (Sí, #etfelicitofill) Els usuaris d'aquest ordinador son gent gran i per no complicar-los la vida vaig simplificar l'inici del grub amb "Ubuntu/Windows".

@kimet Buscaré info sobre el chroot, perquè no en tinc ni idea... 

Demà provaré de remenar amb el Live-CD. Us dic el què, gràcies als dos!

---

### Post by wgarcia on 2010-11-03
Suposo doncs que has tocat els fitxers de configuració del grub perquè sols ensenyi "Ubuntu" i "Windows", sense cap mena d'indicació del menú. Una possibilitat de veure el menú és prémer la tecla de majúscules (la fletxa cap a dalt) durant tot el procés d'arrencada, i si el menú del grub encara està disponible a /boot/grub/grub.cfg, te l'hauria d'ensenyar. Un cop aquí busca la línia d'inici en mode recovery, a veure si pots accedir a la terminal com comentàvem abans.

---

### Post by pablinsfc on 2010-11-03
Gràcies wgarcia. Com dius, vaig modificar les opcions del menú per simplificar-les. El que he fet ara és iniciar amb un Live-CD i modificar de nou el menu.lst del grub perquè em mostri les opcions de recovery i de nuclis antics. Intentaré iniciar així i poder operar amb el terminal.

Salut!

---

### Post by wgarcia on 2010-11-03
Bona idea. Suposo que encara tens el Grub versió 1, perquè a la versió 2 ja no es modifica el menu.lst sinó uns altres fitxers.

---

### Post by pablinsfc on 2010-11-03
Ho he provat però no hi ha manera. He aconseguit veure alguna versió recovery tot i que d'un kernel bastant antic (de fet de la primera versió que hi havia instal·lada al portàtil (8.10). L'he iniciada i després de fer un seguit de comprovacions i posar-ne un parell com a "ARREGLADA", l'inici de l'Ubuntu el feia amb les mateixes linies que posava abans (fallada a mount /dev etc etc).

Ara estic reinstal·lant l'Ubuntu seguint les indicacions d'[aquí]("http://www.uluga.ubuntuforums.org/showthread.php?t=946545"). He guardat el directori /home en un disc extern i fora problemes... us dic alguna cosa.

Moltes gràcies!

---

### Post by pablinsfc on 2010-11-03
Bé, doncs ja ho tinc. He fet la instal·lació de la 10.10 i el tema ha quedat resolt. Ara miraré com s'edita el Grub2 per modificar les opcions d'inici (tot i que en deixaré alguna de recovery per si de cas! ;) ).

Gràcies a tots pel suport!

Salut!

---

