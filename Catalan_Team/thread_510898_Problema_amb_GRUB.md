---
title: "Problema amb GRUB"
date: 2007-07-27
forum: Catalan Team
---

### Post by Ramon P on 2007-07-27
Bones,

sóc un  usuari novell i tot just he aconseguit que el meu modem funcioni en ubuntu; ara bé, no sé perquè tinc un problema amb el GRUB. Vaig fer la instal·lació i ara en iniciar l'ordinador (ja sigui com a primer boot el cdrom o l'HD0) em surt el següent:

Verifying DMI Pool Data...
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21

També haig de dir que si en engegar entro a la BIOS i en surto, llavors ja m'inicia bé, així com si un cop en el sistema el reinicio.

Gràcies per les respostes.

Ah, me'n descuidava. Alguna vegada se m'ha tallat la connexió a Internet i no sé com reconnectar (se'm connecta a l'iniciar el sistema). Bé, potser són preguntes ximples però...

---

### Post by ilku on 2007-07-27
Hola company:
No en se gaire però mirat això
[http://www.ubuntu-es.org/index.php?q=node/52855]("http://www.ubuntu-es.org/index.php?q=node/52855")
I respecte a la connexió ens hauries de donar més informació: amb dhcp, targeta de xarxa, etc (ja saps les coses típiques).
Aquí hi ha gent que segur en sap més i et podrà ajudar força.

---

### Post by Ramon P on 2007-08-10
Bé, veig que no hi ha molta esperança per l'inici.... potser amb LILO?

Pel que fa a internet, tinc la connexió de telefonica estàndard d' 1M a través de modem usb speedtouch 330. Tinc ip dinàmica amb configuració autòmatica dchp.

PD: després de molts maldecaps amb Xserver i amb les vores de les finestres, he aconseguit que Compliz em vagi bé, molt maco. I en el procés he anant aprenent cosetes.... ara m'agrada.

---

### Post by CarlesOriol on 2007-08-11
Probablement és un problema a la bios de l'ordinador.

Mira si pots trobar alguna actualització.

---

### Post by papapep on 2007-08-11
He vist en un post antic que algú ho va sol·lucionar anant a la bios i passant la configuració del disc d'arrancada de "Auto" a "User".

No sé si et funcionarà.

---

### Post by papapep on 2007-08-15
En Cubells acaba de contestar a la llista de la comunitat un problema semblant. No sé si et servirà (edito el post, donat que en Cubells s'ha auto-rectificat :-)):

> El grub està instal·lat al mbr del primer disc perquè si no ho estigués 
arrencaria directament windows...

Jo el que faria seria agafar un livecd, muntar el segon disc al livecd, 
modificar el menu.lst i posar-li el disc correcte al grub, perquè crec 
que segurament el grub s'ha fet un lio detectant els discos...

Des del livecd, una cosa així:

$ sudo su
# mkdir /media/segon_disc
# gedit /media/segon_disc/boot/grub/menu.lst

Aleshores comentaria la línia corresponent al kernel que té en aquest 
moments el grub i la copiaria igual canviant
root=UUID=571e52e2-7032-47cb-a654-bf8bb69f3141
per
root=/dev/sdb1

Desaria els canvis i intentaria arrencar de nou.

Més cap a dalt del primer kernel que arrenca, veuràs una línia on posa 
quelcom així (baix de ### BEGIN AUTOMAGIC KERNELS LIST):
# kopt=root=UUID=571e52e2-7032-47cb-a654-bf8bb69f3141 ro

Aquest UUID es correspon amb l'uuid que tens a la primera línia del kernel??

Adjunta si no ho entens el fitxer aquest /boot/grub/menu.lst del linux 
que tens instal·lat al segon disc (no el del livecd...)

---

