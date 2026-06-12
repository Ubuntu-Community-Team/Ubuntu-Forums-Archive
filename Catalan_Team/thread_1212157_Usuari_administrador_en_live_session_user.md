---
title: "Usuari administrador en live session user"
date: 2009-07-13
forum: Catalan Team
---

### Post by Espigall on 2009-07-13
Bon dia,
Per poder actuar com ususari administrador des del Live Cd o en el meu cas des del USB pre instal.lat del Ubuntu 9.04 com ho puc fer?

Per cert que aquest USB el vaig adquirir a la les Jornades de programari lliure de la UB concretament a la comunitat d-ubuntaires. Anim a tot l-equip!

Concretament necesito poder accedir i editar al boot/grub/menu.lst
No he aconseguit trovar la manera de fer-ho, em denega el permis. 
Si per exemple faig

cd /root     Permis denegat

Insisteixo em pasa des del USB live sesion user.
Tamb'e he provat de crear un nou usuari amb tots el privilegis possibles pero res, continuo sense poder accedir. Que puc fer?
Gr[acies

---

### Post by DaGrimReefah on 2009-07-13
&#65279;Hola. Em disculpo si sóc dur d'entendre. No parlo català, i això es tradueix.

Ha provat "sudo nautilus"? Esperançadorament, hauria de ser capaç d'accedir a la "grub.list" des d'allà. Si vostè pot no, suggereixo caure a l'"apuntador|avís de closques|petxines d'arrel" i escriure:
"nano ~/grub.list"
Espero que això l'ajudi.

---

### Post by papapep on 2009-07-13
Després de recuperar-me de la traducció automàtica de l'apunt de DaGrimReefah (thanks a lot for trying to help in catalan :D)

> Ha provat "sudo nautilus"? Esperançadorament, hauria de ser capaç d'accedir a la "grub.list" des d'allà. Si vostè pot no, suggereixo caure a l'"apuntador|avís de closques|petxines d'arrel" i escriure:
"nano ~/grub.list"

Espigall: et diria que fessis Alt+F2, et surtirà una finestreta, i podràs ficar-hi "gksudo nautilus", el gestor de fitxers amb drets d'administrador (o sigui que compte amb el que fas, que pots fer moltes destrosses), anar i editar /boot/grub/menu.lst .

PS No cal que també t'esmenti que vagis amb MOLT de compte amb què fas amb el menu.lst, pots deixar el sistema inaccesible

---

### Post by Espigall on 2009-07-13
Gracies per les vostres aportacions  DaGrimReefah  i Papapep

He provat el Nautilus. Sembla que dona accés als fitxers del Live USB pro no puc accedir a una de les particions de un disc dur. Al explorador de fitxers sembla restringit a la unitat que ha carregat el Ubuntu.
En la particio hi ha insta.lat un Ubutu 9.04 i amb Nautilus em sembla que no puc anar_hi

Potser faria falta un altre forma d acces

Salutacions

---

### Post by papapep on 2009-07-13
Espigall, company, com ja vàrem comentar a les JPL, una de les mancances de la comunicació escrita és que no ens permet veure la teva pantalla, i jo no he entès què vols dir amb aquest paràgraf:

> He provat el Nautilus. Sembla que dona accés als fitxers del Live USB pro no puc accedir a una de les particions de un disc dur. Al explorador de fitxers sembla restringit a la unitat que ha carregat el Ubuntu.
En la particio hi ha insta.lat un Ubutu 9.04 i amb Nautilus em sembla que no puc anar_hi

Crec que seria necessari que ens fessis cinc cèntims del que et portes entre mans i igual serà més pràctic per a poder-te ajudar amb coneixement de causa. Explica què has fet, i què et passa per haver d'editar el menu.lst, quina configuració de discs o particions tens a l'ordinador, etc...així serà molt més fàcil fer-nos una idea de la situació i buscar una solució correcta i el més simple possible.

També et recomano passar-te pels dos fils de capçalera, un per a presentar-te a la tropa, i l'altre per a fer una llegida a com intentem funcionar. Ànims! ;)

---

### Post by indiosincracia on 2009-07-13
Jo entenc simplement que has de "muntar" la partició a la que vols accedir, res més, he rigut molt amb les aportacions culinaries, en fi, veig que les màquines continuen sent màquines, estic tranquil...
Salut!

---

### Post by Espigall on 2009-07-14
> **papapep said:**
> Espigall, company, com ja vàrem comentar a les JPL, una de les mancances de la comunicació escrita és que no ens permet veure la teva pantalla, i jo no he entès què vols dir amb aquest paràgraf:

Crec que seria necessari que ens fessis cinc cèntims del que et portes entre mans i igual serà més pràctic per a poder-te ajudar amb coneixement de causa. Explica què has fet, i què et passa per haver d'editar el menu.lst, quina configuració de discs o particions tens a l'ordinador, etc...així serà molt més fàcil fer-nos una idea de la situació i buscar una solució correcta i el més simple possible.

També et recomano passar-te pels dos fils de capçalera, un per a presentar-te a la tropa, i l'altre per a fer una llegida a com intentem funcionar. Ànims! ;)

Bon dia,
Vaig fer la llegida al funcionament d'aquest foro abans d'apuntar-me a la comunir¡tat. No em vaig presentar deixan-ho per algun moment de mes inspiració pero ara ja ho he fet. [IMG]http://ubuntuforums.org/images/icons/icon14.gif[/IMG]

El que em porto entre mans, consisteix en que tinc un PC fix amb 2 discs durs del que he hagut de reinstal.lar el finestres i aprofitant l'avinentesa fer engegada dual amb UBUNTU. 
Tan bon punt vaig haver instal·lat i provat el finestres, amb el Gparted he reduit la partició del finestres deixant un espai vuit.
Per cert, el finestres m'ha denominat el disc d'arranc com D: deixan el disc de dades com C: (es una dada, al finestres no dona cap problema de moment).
A continuació he instal·lat el ubuntu cedint l'espai vuit per que el instal.lador crei les 2 típiques particions. Això ja ho he fet amb altres instal.acions i ha anat be.
Al arrancar no surt el Grub i arranca tan sols el finestres.
A partir d'aquí he estat buscant i dedicant molt temps a aquest problema i una de les sol.lucions que m'ha semblat mes be i entenible per mi es modificar l'arxiu /boot/grub/menu.lst del Ubuntu instal·lat a la partició del disc dur per veure si aconsegueixo fer sortir el Grub. El primer problema era que no em deixava editar l'arxiu menu.txt i a partir d'aquí el que ja he dit...
Evidentment que això ho haig de fer necessàriament iniciant l'ordinador amb un live i que el Nautilus m'ha permès poder accedir als arxius de sistema del live pero en cap cas al disc dur, això es el que volia dir.
Suposo que el problema que tinc es pot resoldre d'altres formes, pro el meu nivell amb el monitor, SUDO i moltes altres coses que he llegit, es de primària, pro no defallejo en anar aprenent i provant. Per cert, en aquests moments un concepte tan repetit i tocat com 'muntar la partició' encara no se ben be que significa....
Resto molt obert a altres camins per solucionar aquest problema.

salut  ):P

---

### Post by papapep on 2009-07-14
Collonut, Espigall, ara ja sabem tots plegat on som ;)

Ara caldria una miqueta d'informació del teu ordinador. Fes a un terminal del CD viu aquest que manegues:

```
sudo fdisk -l
```

i també:

```
cat /etc/fstab
```

i enganxa'ns aquí el que et surti com a resposta de les ordres i veurem com tens repartides, i a quins discs, les particions.

Muntar les particions significa que les particions (divisions lògiques) que té un disc dur siguin accessibles al sistema operatiu. És, per a fer-ho més didàctic, com si les poguessis posar en estat ON i OFF a voluntat. Muntar (ON) quan són accessibles, i desmuntar (OFF) quan hi són, però no s'hi pot accedir. La diferència respecte els Win és que en aquest sempre són muntades, i a Gnu/Linux poden estar-ho o no, sempre que no sigui amb la que estàs treballant en aquell moment, clar...
A més, al sistema operatiu li cal un "punt de muntatge", que no és més que un lloc del sistema de fitxers al qual tu li dius que vols trobar aquesta partició.

Un símil cutre i limitat són les unitats (C:, D:, etc.) de Win.

Un exemple: tu tens un disc que vols dedicar només a posar-hi música, que resulta que és el dispositiu /dev/sdd (el nom li posa solet l'Ubuntu) i només té una partició: /dev/sdd1.

Aleshores, tu pots decidir que vols que t'apareguin aquestes dades a /home/elteuusuari/megalomania. Crees el directori aquest:

```
mkdir /home/elteuusuari/megalomania
```

i el muntes quan vulguis per a fer accessible la música que hi tens:

```
sudo mount /dev/sdd1 /home/elteuusuari/megalomania
```

a partir d'aquest moment, si vas a /home/elteuusuari/megalomania hi trobaràs tot el que tinguis dins el disc on deses la música.
Si fas:

```
sudo umount /dev/sdd1 /home/elteuusuari/megalomania
```

La música, evidentment, seguirà allà, però ja no serà accessible (fins que el tornis a muntar, clar :D). Això pot semblar una tonteria, però és tremendament útil quan et cal fer alguna feina ala sistema de fitxers i no vols haver d'aturar i reiniciar l'ordinador.

Evidentment, això s'automatitza per a no haver d'anar muntant i desmuntant discs cada cop, però la base segueix com t'ho he explicat.

Espero haver-me sapigut explicar.

---

### Post by Espigall on 2009-07-14
Gràcies per la teva inestimable info Papapep. Crec que per fi he entes el que significa i per que serveix muntar. 

En quan al codi:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disc /dev/sda: 160.0 GB, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x120f120e

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       11791    94711176    7  HPFS/NTFS
/dev/sda2           11792       19457    61577145    5  Estesa
/dev/sda5           11792       19138    59014746   83  Linux
/dev/sda6           19139       19457     2562336   82  Intercanvi Linux / Solaris

Disc /dev/sdb: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9aabbed2

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS

Disc /dev/sdc: 2100 MB, 2100297728 octets
65 heads, 62 sectors/track, 1017 cylinders
Units = cilindres of 4030 * 512 = 2063360 bytes
Disk identifier: 0x000e6059

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdc1   *           1        1017     2049224    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$
``````
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0
ubuntu@ubuntu:~$
```Be suposo que es això el demanes.

salut

---

### Post by papapep on 2009-07-14
Curiós. Tens les particions amb el linux i la swap:

> /dev/sda5           11792       19138    59014746   83  Linux
/dev/sda6           19139       19457     2562336   82  Intercanvi Linux / Solaris


però no les tens al /etc/fstab que és on es diu quines particions es volen muntar, i a quin punt de muntatge, a l'arrencada de l'ordinador:

> ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0


Per a que s'entengui més, fixa't en el que tinc jo:

```
papapep@awacs:~$ sudo fdisk -l
[sudo] password for papapep: 

Disc /dev/sda: 60.0 GB, 60011642880 octets
255 heads, 63 sectors/track, 7296 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
[COLOR="Blue"]**/dev/sda1**[/COLOR]   *           1        2432    19535008+  83  Linux
[COLOR="Red"]**/dev/sda2**[/COLOR]            2433        7052    37110150   83  Linux
[COLOR="Lime"]**/dev/sda3 **[/COLOR]           7053        7296     1959930   82  Intercanvi Linux / Solaris

```

i

```
papapep@awacs:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on [COLOR="Blue"]**/dev/sda1**[/COLOR] during installation
UUID=00436e4c-e831-42c0-9b51-38e7cd3bae14 /               ext4    relatime,errors=remount-ro 0       1
# /home was on [COLOR="Red"]**/dev/sda2**[/COLOR] during installation
UUID=01e2965c-876e-4609-89eb-ea98addedb80 /home           ext3    relatime        0       2
# swap was on [COLOR="Lime"]**/dev/sda3**[/COLOR] during installation
UUID=3a7dcf48-24bf-4159-a224-c04d95dcd797 none            swap    sw              0       0

```

Per cert, pel tema del grub, has provat ja a fer un?:

```
sudo update-grub
```

PS Punyetes....el "cat /etc/fstab" l'has fet des d'un CD viu...i mostra el fstab del CD viu, no del disc dur, que és el que volia veure jo.

---

### Post by papapep on 2009-07-14
Fes a un terminal:

```
mkdir /home/elteuusuari/disc-dur
```


```
sudo mount /dev/sda5 /home/elteuusuari/disc-dur
```

si vas a /home/elteuusuari/disc-dur, trobaràs tota l'estructura del sistema de fitxers del disc dur on tens el linux instal·lat. Ara podràs fer:

```
cat /home/elteuusuari/disc-dur/etc/fstab
```

que és el que necessitem veure :)

---

### Post by Espigall on 2009-07-14
Ja he fet
sudo update-grub 
Ha dit que no existeix, i sembla lógic ja que en el 'viu' no hi ha grub.

Abans de rebre el teu segon escrit he buscat la forma d'accedir al arxiu /etc/fstab visualitzant l'arxiu pel menu 'Llocs' del disc a on hi ha el Ubuntu  i he obtingut el text que busquem:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1a326282-9b76-40a4-96ef-5fae422862cb /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=04a47433-a678-4fa2-ac84-071e401fed6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```Vejam si et dona alguna pista i podem trovar solució.
Salut

---

### Post by Espigall on 2009-07-16
Bon dia,
No he aconseguit des  del CD 'viu' editar arxius de una una instal.lacio de Ubuntu que mai no ha arrancat a causa de no funcionar el Grub.

Al final crec que he entès el problema i consistia en una configuració de la BIOS que feia que el MBR es situes sempre al segon disc hdb0 i al instal.lar win ubicat al primer hda0 juntament amb la partició Ubuntu hda1 , al arrencar el MBR direccionava el Win i no trovava el Grup.

Solució: Modificar la Bios posan el primer disc com Boot i definin com a primer el mateix i reinstal.lació de win i Ubuntu. i ok :razz:

Salut!

---

