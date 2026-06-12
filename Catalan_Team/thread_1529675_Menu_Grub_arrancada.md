---
title: "Menu Grub arrancada"
date: 2010-07-12
forum: Catalan Team
---

### Post by carlesbm on 2010-07-12
Hola ha tots

    Estic buscant ajuda per intentar de solucionar un problema amb el Grub, us explico:

    En el meu ordinador tinc instal·lat Ubuntu 10.04 i Windows Xp, be; fa uns dies que vaig realitzar l'actualització de la 9.10 a la versió 10.04, la instal·lació va anar tot correcte, unicament destacar que en el moment de la configuració del Grub poder hem vaig fer una mica, un embolic, però vist que despres tot va funcionar be , hem refereixo ha que Ubuntu va arrencar amb tota la normalitat, no vaig probar Windows. Arribat un dia que la vaig haver de arrancar Windows per tal de utilitzar una aplicació, i la meva sorpresa es que la pantalla es queda amb el cursor _ a la part superior esquerra i la pantalla negra. Proces;

    Arancar el PC apareix el menu del Grub i selecciono la opció de altres SO Windos Xp en /sdb1

    Que es elq ue ha passat?
    Vaig posar el grup en el disc equivocat?
    Hi ha solució sense haver de fer cap format?

   Porto tota la setmana cercant informació a internet i no en trec l'entrallat.

    Us agraeixo molt que hem pugueu ajudar.

Moltes Gracies

---

### Post by wgarcia on 2010-07-12
Hi ha un error seriós (crític) amb el component OS Prober del Grub que fa que no es detectin correctament els altres sistemes operatius. Ja estan preparats els pegats per arreglar-ho, però encara no s'ha fet l'actualització. 

El més probable és que ara l'entrada del Grub que tens estigui apuntant a la partició "recovery" del windows i no la que té la teva instal·lació. 

Per corroborar, fes 

sudo update-grub 

des de la terminal i mira quin disc identifica per al windows, i després fes

sudo fdisk -l 

i mira si correspon a on està realment instal·lat el windows. Si tens dubtes sobre com interpretar aquests resultats engantxa'ls aquí al fòrum.

---

### Post by carlesbm on 2010-07-12
Hola i bona nit

   He realitzat els passos que m'has indicat wgarcia

Aquí enganxo el resultat.

carles@carles:~$ sudo update-grub
[sudo] password for carles: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done
carles@carles:~$ sudo fdisk -l

Disc /dev/sda: 120.0 GB, 120034123776 octets
255 heads, 63 sectors/track, 14593 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48459674

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Estesa
/dev/sda5           13996       14593     4803403+  82  Intercanvi Linux / Solaris

Disc /dev/sdb: 250.1 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x092d092d

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS

Disc /dev/sdc: 4022 MB, 4022337536 octets
128 heads, 63 sectors/track, 974 cylinders
Units = cilindres of 8064 * 512 = 4128768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdc1               1         975     3930652    b  W95 FAT32
carles@carles:~$ 

   Cal dir que fisicament hi ha 2 disc durs i un Pen-USB conectat actualment.

 Moltes gracies

---

### Post by wgarcia on 2010-07-13
Doncs no sembla que sigui l'error que mencionava, perquè no hi ha més que una partició amb windows, pel que sembla. Una altra possibilitat és que s'hagi instal·lat el grub al MBR on estava l'arrencada de windows i ara no pugui arrencar aquest sistema operatiu. 

Mira de fer el que explico en aquest comentari:

[http://ubuntuforums.org/showpost.php?p=9323683&postcount=22](http://ubuntuforums.org/showpost.php?p=9323683&postcount=22)

Engantxa en un fitxer els resultats i adjunta'ls aquí, aquest programeta dóna molta informació sobre la disposició de les particions i on està gravat el grub.

---

### Post by carlesbm on 2010-07-16
Hola de nou

    Disculpeu la tardança però he estat una mica liat amb la feina.

He executat el arxiu que m'has dit wgarcia i aquí t'adjunto el arxiu Resultat.txt

---

### Post by wgarcia on 2010-07-17
Segons el que em sembla que es pot veure al teu RESULT.txt el problema és que el "grub", el sistema per arrencar des de les diverses particions, s'ha escrit al "MBR" (master boot record) del disc on tens instal·lat el Windows XP, sobreescrivint els arxius d'arrencada de Windows XP. 

Per tant el que es tracta és de tornar a escriure aquests arxius d'arrancada de Windows XP al MBR del disc /dev/sdb1 . 

MOLT IMPORTANT: Abans de res fes còpia de totes les dades importants que tinguis tant a Ubuntu com a Windows. Per accedir als continguts de Windows munta la seva partició des d'Ubuntu i fes còpies de tota la informació que hi ha. 

Per tant compte amb les instruccions de recuperar arrencada per no perdre cap dada important, i tot el que facis sempre sota la teva pròpia responsabilitat. 

Les instruccions que es poden trobar als fòrums sobre com recuperar l'arrencada de Windows són les següents (I SENSE GARANTIES PERQUÊ NO HE PROVAT):

1) S'ha d'insertar el disc d'instal·lació de Windows XP i iniciar l'ordinador amb el disc posat (si arrenca directament el disc dur s'ha d'entrar en la configuració inicial i veure si està posat el CD com a opció d'arrencada inicial abans que el disc dur). 

2) El disc de windows et preguntarà si vols reparar/recuperar, i s'ha d'escollir "r". Potser demani clau d'administrador.

3) Hauria de sortir una línia de comandes, on s'han d'entrar les comandes següents:

fixboot

fixmbr

exit

4) Es remou el disc d'instal·lació de XP i es reinicia. 


Ara bé, no em queda clar si aquest procediment sobreescriu el grub, potser algú ho pot aclarir aquí, cosa que faria que ara no arrenqués l'Ubuntu... Penso que no, perquè el format de les particions on hi ha l'Ubuntu és ext4 i el Windows no pot llegir aquest format. En cas que es sobreescrigués el Grub, es pot recuperar fàcilment des d'un LIVE CD d'Ubuntu, però això és una altra història.

---

### Post by carlesbm on 2010-07-17
Moltes gracies per la teva ajuda i consells, aquest fi de setmana probaré de fer aixoó que hem dius, espero que tot hem vagi bé.


Moltissimes Gracies
;):-k

---

