---
title: "No puc entrar al meu kubuntu"
date: 2010-12-28
forum: Catalan Team
---

### Post by miquelet on 2010-12-28
Hola a tothom,

Tinc un portàtil amb l'xp i el kubuntu 10.10.  Des de l'última vegada que vaig fer update i upgrade que em passa el següent: quan vull entrar al kubuntu, com sempre m'apareix la pantalla perquè faci la identificació (nom i contrasenya), però llavors no em responen ni el ratolí ni el teclat.  (el kernel que m'apareix en primer lloc és el 2.6.35-22-generic; ho dic per si pot ser una informació útil).  Què puc fer? Moltes gràcies.

---

### Post by quitus on 2010-12-28
Per començar pots provar a arrencar amb un kernel antic, a veure si funciona.

---

### Post by miquelet on 2010-12-28
Ja ho he provat, i no funciona.

---

### Post by wgarcia on 2010-12-29
Si tens un CD d'Ubuntu (Live CD) prova d'arrencar amb aquest CD a veure si en la sessió de prova d'Ubuntu es reconeixen el teclat i el ratolí, si fos el cas podria ser que hi ha alguna configuració malament a la teva instal·lació actual, com per exemple controladors incorrectes per a la teva targeta gràfica.

---

### Post by orestesmas on 2010-12-29
Pots provar d'escollir el kernel de recuperació. Això et deixarà en una consola en mode texte i suposo que allí si que et funcionarà el teclat. Entres i mira el directori /etc/X11. Allí hi trobaràs uns fitxers del tipus xorg.conf*, que són els que es fan servir per indicar a les X alguns paràmetres de configuració diferents dels paràmetres per defecte. Mira si hi ha un fitxer xorg.conf.bak (o similar) que ésla còpia de seguretat del que tenies abans (i que funcionava). 

Si veus diferències entre aquest i el d'ara (xorg.conf), pots copiar l'antic sobre el nou

```
cp xorg.conf.bak xorg.conf
```

 i reiniciar, a veure si s'arregla...

---

### Post by miquelet on 2010-12-29
Potser això que proposes, Orestes, és massa complicat per mi.  ¿Escollir el kernel de recuperació vol dir entrar en "recovery mode"?  Si és això, ja ho he provat i no em deixa escriure.

D'altra banda, quan tinc el menú per escollir kernel em dóna l'opció (c) d'entrar en consola (GRUB); però llavors no sé quina ordre li he de donar.  Uf, potser el més senzill és provar d'entrar amb el Live-CD, copiar home i reinstal·lar el Kubuntu.  Gràcies de totes maneres.  A poc a poc vaig entenent millor què li pot haver passat.

---

### Post by wgarcia on 2010-12-29
Abans de reinstal·lar, si des del Live CD tens accés al teclat i al ratolí potser encara es pugui fer alguna cosa sense reinstal·lar.

---

### Post by miquelet on 2010-12-29
Sí que hi he pogut entrar i em responen el ratolí i el teclat i he pogut accedir a les diferents carpetes (la wifi, però, no em va).  Ho he fet amb un Live CD de la 10.04, tot i que jo hi tinc la 10.10.  Amb la 10.10, des que hi vaig fer l'actualització, he tingut alguns problemes (segur que més culpa meva que d'ella) i ja havia decidit, en el cas que no pogués sortir-me'n d'aquest problema, d'instal·lar-hi la 10.04, que crec recordar que m'anava molt bé.  És per això que, tenint el Live CD de la 10.04 a punt, ho he provat i hi he pogut entrar.  Això, ara, és important?  

Bé, que hi he entrat.  I ara què hauria de fer?  Moltes gràcies.

---

### Post by wgarcia on 2010-12-30
Bé, el que no podràs fer és "desactualitzar" des de la 10.10 cap a la 10.04, en aquest cas hauràs de fer una instal·lació nova. 

Però encara es pot mirar el que va suggerir l'orestesmas. Primer s'haurà de muntar des del Live CD els teus discos. Per veure això primer fes des d'una terminal (a dins del Live CD): 

sudo fdisk -l

això permetrà veure on tens instal·lada la 10.10.

---

### Post by miquelet on 2010-12-30
Després de fer el que m'has dit, em diu:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disc /dev/sda: 250.1 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x52305230

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        6625    53215281    7  HPFS/NTFS
/dev/sda2            6626       30401   190980720    f  W95 Estesa (LBA)
/dev/sda3           29648       30401     6056473+  82  Intercanvi Linux / Solaris
/dev/sda5            6626       29647   184924152   83  Linux

---

### Post by wgarcia on 2010-12-30
Llavors ara, es poden entrar les següents línies des d'una terminal, per veure si hi ha una versió anterior de l'arxiu xorg.conf com suggeria l'orestesmas:

sudo mkdir /mnt/disc

sudo mount /dev/sda5 /mnt/disc

ls /mnt/disc/etc/X11


sempre prement "intro" després de cada línia. El que fan aquestes comanda és crear una carpeta dins de "/mnt", muntar el teu disc d'ubuntu a aquesta carpeta, i llistar els fitxers a /etc/X11 que ens permetrà veure si hi ha fitxers de configuració xorg.conf . 

Engantxa aquí el resultat que produeixi l'última línia.

---

### Post by miquelet on 2010-12-30
M'ha sortit això:

ubuntu@ubuntu:~$ ls /mnt/disc/etc/X11
app-defaults  default-display-manager  rgb.txt  xinit                       Xreset     Xresources  Xsession.d            XvMCConfig
cursors           fonts                                X          xorg.conf.failsafe  Xreset.d  Xsession      Xsession.options  Xwrapper.config

Per bé que ordenat d'una altra manera, perquè el copiar i enganxar ha modificat les línies.

---

### Post by wgarcia on 2010-12-31
Ara hauries d'enganxar, si és possible en un fitxer adjunt de text, el que et surti quan entres a la terminal:

cat /mnt/disc/etc/X11/xorg.conf.failsafe

---

### Post by miquelet on 2010-12-31
Em diu "No such file or directory".  Mmmmmm.

---

### Post by wgarcia on 2011-01-01
Poden haver passat dues coses:
1) no has tornat a muntar /mnt/disc seguint els passos que ja vas fer un cop

2) no has entrat exactament la instrucció

perquè el fitxer està allí i el missatge que et surt no hauria de sortir.

---

### Post by miquelet on 2011-01-01
No havia tornat a muntar el disc.  Adjunto el que m'ha sortit. (I bon any!).

---

### Post by wgarcia on 2011-01-01
Sembla que el teu problema no ve d'una configuració incorrecta del sistema gràfic, que en versions antigues també configurava els dispositius d'entrada tipus teclat o ratolí.

Quin tipus de teclat i ratolí tens? Es connecten per USB o usen les connexions PS/2 (les rodones tradicionales)?

---

### Post by miquelet on 2011-01-01
És un portail Hp pavillion

---

### Post by wgarcia on 2011-01-01
Llavors el ratolí és USB o és un dispositiu integrat a l'ordinador?

---

### Post by miquelet on 2011-01-01
És integrat.

---

### Post by wgarcia on 2011-01-01
Es pot provar una altra estratègia, consistent en intentar entrar sense interfície gràfica i reconfigurar/reinstal·lar un parell de coses. Potser algú que faci servir kubuntu també pot suggerir alguna altra cosa.

Per fer això prova el següent. Inicia l'ordinador, i quan surti el menú de grub per escollir el sistema a entrar prem la tecla "e". Això et permetrà editar la línia d'arrencada per un sol cop. 

Veuràs una sèrie de línies, i amb la fletxa "cap avall" ves fins a una línia que comença amb "linux /boot/vmlinuz...". Prem la tecla "Fin" i posa't al final de la línia. Amb la tecla d'esborrar elimina "quiet splash" i escriu "single". Després prem "Control X" (la tecla control i la tecla X) i el sistema hauria d'arrencar. Et mostrarà totes les instruccions que fa per arrencar, de pas si veus alguna que posi error mira si la pots capturar.

Després de moltes línies arribarà a un menú on has d'escollir l'opció que comença amb "netroot". 

Un cop que facis això sortirà una pantalla de text on et mostrarà una cosa com:

root@ordinador-miquelet:-$

Aquí es pot intentar reconfigurar el sistema gràfic, sempre suposant que el teclat funcioni:

sudo dpkg-reconfigure xserver-xorg

i reinstal·lar el gestor d'entrada de kubuntu:

sudo apt-get install --reinstall kdm

Un cop que acabi intenta entrar

sudo service kdm start

i a veure si arriba a la pantalla d'entrada amb teclat i ratolí funcionant.

---

### Post by miquelet on 2011-01-01
Fins al Ctrl X he seguit els passos, però després de les nombroses línies m'ha quedat la pantalla amb això

[     2.473423] Console: switching to colour frame buffer device 160x50
[     2.478407] fb0:  inteldrmfb frame buffer device
[     2.478709] drm: registered panic notifier
[     2.478793] Slow work thread pool:  Starting up
[     2.478990] Slow work thread pool:  Ready
[     2.483745] acpi device: 08: registered as cooling_device2
[     2.484274] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A0B/LNXVIDEO:01/input/input5
[     2.484405] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
[     2.484690] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[     2.708034] Skipping EDID probe due to cached edid

I aquí ja no hi puc fer res, el teclat només em respon per fer un ctr+alt+supr per reiniciar.

---

### Post by kimet on 2011-01-01
Des de el live cd també es pot reconfigurar el servidor x.
Muntes el dispositiu i fas.
```
chroot /mnt/disc
```
Des de aquí pots fer depres el dpkg-reconfigure xserver-xorg.

Salut i bon any a tots.

---

### Post by miquelet on 2011-01-01
Finalment s'ha solucionat el problema.  Crec que la solució ha estat  poder fer el dpkg-reconfigure xserver-xorg des del Live CD.  Moltes gràcies a tots per l'ajuda.  Bon any, salut i sort!!!

---

### Post by pablinsfc on 2011-01-02
Hola a tots! He tingut el mateix problema amb un Dell Inspiron 1564 + Ubuntu 10.10 i efectivament amb un Live-CD o amb un teclat/ratoli per USB fent el dpkg-reconfigure xserver-xorg el problema ha quedat resolt! Moltes gràcies!!

Salut i Bon any!

PD. Proposaria canviar el títol a quelcom semblant a "No respon teclat i ratolí" o similar.

---

### Post by miquelet on 2011-01-02
Em sembla bona idea el que em proposes de canviar el nom del fil.  Com ho he de fer?

---

