---
title: "Arrencada congelada"
date: 2011-05-23
forum: Catalan Team
---

### Post by LitusMayol on 2011-05-23
Bones!

Feia temps que no treia el cap per'quí, eh!

Últimament tenia el tema actualitzacions una mica deixat (encara anava amb la 10.04). Vaig decidir actualitzar.

Em va fer passar primer a la 10.10. Vaig suposar que era lo normal, primer instal·lar la 10.10 i després tornar a actualitzar a la 11.04.

La instal·lació sense cap problema. Reinicio... i em quedo sense ordinador. 

Em surt una pantalla lilosa amb les lletres de "Ubuntu 10.10", els quatre quadradets de carrega i em diu :
> 
Your disk drives are being checked for errors. This may take some time


Premeu C per canel·lar totes les comprovacions en curs

Si no faig res, no acaba mai.

Si premo C, canvia la pantalla.El missatge és el següent:
> S'han trobat errors en comprovar la unitat de disc de /

Premeu F per intentar arreglar els errors, I per ignorar-los, S per ometre el muntatge o M per fer una recuperació manual


LES DIVERSES OPCIONS
Si premo F:
> La unitat de disc de /tmp no està preparada o present

Continueu esperant o premeu S per ometre el muntatge, o M per fer una recuperació manual

jo no sé fer la recuperació manual. Per tant o espero o premo S.

Si espero no passa res. Si premo S torno a la pantalla inicial de "Your disk drives are being checked for errors..."


Que faig? :S

---

### Post by wgarcia on 2011-05-24
Mira si el que s'explica en aquest missatge:

[http://ubuntuforums.org/showpost.php?p=10779018&postcount=7](http://ubuntuforums.org/showpost.php?p=10779018&postcount=7)

et pot servir.

---

### Post by LitusMayol on 2011-05-25
Aquesta és la resposta:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003345b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19130   153661693+  83  Linux
/dev/sda2           19131       19457     2626627+   5  Extended
/dev/sda5           19131       19457     2626596   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1: net, 421421/9609216 fitxers, 33008151/38415423 blocs
ubuntu@ubuntu:~$ 

Ara probaré d'arrencar-lo de nou. A veure. (Merci passi el que passi.)

---

### Post by LitusMayol on 2011-05-25
Iep!

Ja ho he probat!


El panorama ha canviat. Ara ja no em diu re de comprovació d'errors al disc, però... Es queda bloquejat en aquella pantalla negra del boot en que a la primera línia diu des de quina unitat està muntant i en la segona hi posa "Starting Up..." i és queda així indefinidament...

---

### Post by wgarcia on 2011-05-25
Tens possibilitat d'entrar en mode recovery?

---

### Post by LitusMayol on 2011-05-26
Hei!

Si que puc. Bé, tinc la opció. Però si arrenco amb Recovery Mode, va més enllà del "Starting Up..." però es queda carregant. Van sortint línies, però cap d'error, i va carregant. Però no s'acaba mai...

---

### Post by wgarcia on 2011-05-26
Potser s'hagi d'arreglar algun altre sistema de fitxers on tens l'arrencada. O potser hi hagi un problema d'instal·lació del menú d'arrencada (grub). 

Hi ha una utilitat força bona i desenvolupada a ca nostra per recuperar l'arrencada, fa la verificació dels discos i permet reinstal·lar el menú d'arrencada grub, es diu Rescatux i l'adreça és:

[http://www.bootproblems.com/](http://www.bootproblems.com/)

Es tracta de crear un CD autònom amb Rescatux i després en entrar et dóna opció de verificar els discos, reinstal·lar el grub, etc.

---

