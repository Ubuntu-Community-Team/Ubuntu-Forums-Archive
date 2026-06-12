---
title: "No puc accedir a la particio windows"
date: 2010-05-06
forum: Catalan Team
---

### Post by pserra on 2010-05-06
Hola, 
em semblava que la instalacio al compaq de la lucid havia anat bé... però no se que em passa que l'engegada dual a windows em falla... em queda en negre...
He provat amb el SUPERGRUP i li faig reparar i queda igual..
Hi ha alguna manera de desmuntar/muntar la particio de windows...potser...(no ho se) així me la reconeixerà...
He provat amb el mount -a i no me l'ha reconegut.....
Resumint:
1-el /etc/fstab el tinc igual que abans de l'actualització
2- si cliko a l'icona computer les particions em surten com la mida total del disc dur
3- a /media em surt la particio i puc accedir-hi (com sempre, normal)
4- la utilitat que m'ha ajudat amb el netbook que es diu "utilitat dels discs" si li dic que em comprovi
la partició em surt l'error: "......... el dispositiu esta ocupat" i si vaig a detalls -->Device is mounted
and no online capability in fsck tool for file system
QUE MÉS PÙC PROVAR??

---

### Post by papapep on 2010-05-06
Fes un: 

```
sudo fdisk -l
```

i enganxa'ns aquí el resultat.

---

### Post by pserra on 2010-05-06
> **papapep said:**
> Fes un: 

```
sudo fdisk -l
```

i enganxa'ns aquí el resultat.


aqui esta:
> pere@pere-portatil:~$ sudo fdisk -l
[sudo] password for pere: 

Disc /dev/sda: 320.1 GB, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9fca1fd5

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       13462   108133483+   7  HPFS/NTFS
/dev/sda2           37632       38913    10292224    7  HPFS/NTFS
/dev/sda3           34640       37631    24033240    5  Estesa
/dev/sda4           13463       34639   170104252+   7  HPFS/NTFS
/dev/sda5   *       34640       35199     4498168+   b  W95 FAT32
/dev/sda6   *       35200       35566     2947896   82  Intercanvi Linux / Solaris
/dev/sda7           35567       37631    16587081   83  Linux

Les entrades a la taula de particions no estan en l'ordre del disc


la particio del windos es la de sda1 i el fdisk -l està igual que abans de l'actualització

---

### Post by papapep on 2010-05-06
Si tens fitxers importants a perdre, el primer que jo faria seria arrencar l'ordinador amb un CD en viu i fer-ne una còpia de seguretat.

Seguidament, un cop feta còpia de tot el que vulguis, provaria a arrencar l'Ubuntu i fer:

```
sudo update-gru**b**
```

això t'hauria de regenerar el menú del Grub i posar-te tots els SSOO.

---

### Post by pserra on 2010-05-06
> **papapep said:**
> Si tens fitxers importants a perdre, el primer que jo faria seria arrencar l'ordinador amb un CD en viu i fer-ne una còpia de seguretat.

Seguidament, un cop feta còpia de tot el que vulguis, provaria a arrencar l'Ubuntu i fer:

```
sudo update-gru**b**
```

això t'hauria de regenerar el menú del Grub i posar-te tots els SSOO.
-Per els documents 'importants' els tinc en una particio de 5gb...penso que no els hauria de perdre
-ahir ja vaig trobar un enllaç i ja vaig fer el  update-grub amb el mateix resultat que avui... se'm queda la pantalla negra quan vull accedir a la particio sda1. Deixo sortida terminal.. m'estranya el que m'està passant...que més puc provar?
> pere@pere-portatil:~$ sudo update-grub
[sudo] password for pere: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
pere@pere-portatil:~$ 
aquesta tarda al fer un update he instal·lat  el vmlinuz-2.6.32-22-generic.... aquest em té la pantalla negra 1 minut... llavors si.. em carrega l'escritori en 5 segons...
trobo que va lent....

---

### Post by wgarcia on 2010-05-06
Penso que l' update-grub sols et regenera els arxius de configuració, però perquè s'instal·lin de debó has de fer 

sudo grub-install /dev/sda

---

### Post by pserra on 2010-05-06
Hola,
que estrany, per provar...
des de el gparted he desmuntat la partició sda1, he provat d'entrar-hi i rés... després l'he activat/muntat des de l'eina de configuració ntfs, i al reiniciar en sda1 ni m'ha sortit rés i al entrar a ubuntu m'ha sortit el missatge que després ha marxat:
udevd-work (362): open /dev/null failet: No such file or directory
no se si pot aportar informació aquest missatge...

---

### Post by pserra on 2010-05-06
> **wgarcia said:**
> Penso que l' update-grub sols et regenera els arxius de configuració, però perquè s'intal·lin de debó has de fer 

sudo grub-install /dev/sda

Merci wgarcia
ho he provat i he quedat igual... deixo terminal:
> pere@pere-portatil:~$ sudo grub-install /dev/sda
[sudo] password for pere: 
Installation finished. No error reported.
pere@pere-portatil:~$ 
qué més puc provar?? es molt estrany...

---

### Post by oriolsbd on 2010-05-06
Per a Linux, no hi ha cap eina que et faci una comprovació completa d'una partició NTFS. Però hi ha el ntfsfix, que fa una comprovació "parcial". En vaig parlar fa uns mesos:
[http://alliberats.cat/comprovacio-i-correccio-derrors-en-particions-ntfs/](http://alliberats.cat/comprovacio-i-correccio-derrors-en-particions-ntfs/)

Salut!

---

### Post by pserra on 2010-05-06
> **oriolsbd said:**
> Per a Linux, no hi ha cap eina que et faci una comprovació completa d'una partició NTFS. Però hi ha el ntfsfix, que fa una comprovació "parcial". En vaig parlar fa uns mesos:
[http://alliberats.cat/comprovacio-i-correccio-derrors-en-particions-ntfs/](http://alliberats.cat/comprovacio-i-correccio-derrors-en-particions-ntfs/)

Salut!
ho he provat:

> pere@pere-portatil:~$ sudo ntfsfix /dev/sda1
Refusing to operate on read-write mounted device /dev/sda1.
pere@pere-portatil:~$ sudo ln -s /usr/bin/ntfsfix /sbin/fsck.ntfs
pere@pere-portatil:~$ sudo fsck /dev/sdxx
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory en intentar obrir /dev/sdxx

No s'ha pogut llegir el súperbloc, o bé no descriu un sistema de fitxers
ext2 correcte. Si el dispositiu és vàlid i realment conté un sistema de fitxers
ext2 (i no pas d'intercanvi, ufs o algun altre), llavors el súperbloc
està malmès, per la qual cosa podeu provar d'executar l'e2fsck amb
un súperbloc alternatiu:
    e2fsck -b 8193 <dispositiu>
pere@pere-portatil:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs-3g: not found
fsck: Error 2 while executing fsck.ntfs-3g for /dev/sda1
pere@pere-portatil:~$ 
La sortida es aquesta...

---

### Post by wgarcia on 2010-05-06
El Windows Vista porta una imatge per regenerar la instal·lació, i la instal·lació pròpiament dita. La partició amb la imatge està normalment abans de la particició amb la instal·lació. No serà que la instal·lació real la tens en /dev/sda2? Suposo que no serà això, perquè ja arrencaves el W.V. de la /dev/sda1, oi?

---

### Post by pserra on 2010-05-06
> **wgarcia said:**
> El Windows Vista porta una imatge per regenerar la instal·lació, i la instal·lació pròpiament dita. La partició amb la imatge està normalment abans de la particició amb la instal·lació. No serà que la instal·lació real la tens en /dev/sda2? Suposo que no serà això, perquè ja arrencaves el W.V. de la /dev/sda1, oi?

Merci wgarcia,
per la mida de la particio ha de ser sda1, però de totes maneres he reiniciat... i he seleccionat sda2 i fa el mateix (REEES) la pantalla negre.....
que més puc probar?? necessito d'alguna aplicació del windos...
A ningú més li ha passat??

merci...

---

### Post by oriolsbd on 2010-05-07
Hola, quan has executat el "ntfsfix", t'ha donat problemes perquè tenies la partició muntada. Primer, mira que no estiguis accedint a aquesta partició. Sent la de Windows, si no tens cap programa amb un fitxer d'aquesta partició obert (per exemple, algun document) i si no hi estàs navegant des del Nautilus, no hi hauria d'haver problema.

Després, desmunta la partició, torna a executar el "ntfsfix" i torna a muntar la partició:
```
sudo umount /dev/sda1
sudo ntfsfix /dev/sda1
sudo mount /dev/sda1
```

A veure què et diu.

Per cert, veig que també hauries de crear aquest enllaç per tal que l'ntfsfix et funcioni amb fsck:
```
sudo ln -s /usr/bin/ntfsfix /sbin/fsck.ntfs-3g
```

Salut!

---

### Post by pserra on 2010-05-07
> **oriolsbd said:**
> Hola, quan has executat el "ntfsfix", t'ha donat problemes perquè tenies la partició muntada. Primer, mira que no estiguis accedint a aquesta partició. Sent la de Windows, si no tens cap programa amb un fitxer d'aquesta partició obert (per exemple, algun document) i si no hi estàs navegant des del Nautilus, no hi hauria d'haver problema.
Després, desmunta la partició, torna a executar el "ntfsfix" i torna a muntar la partició:
```
sudo umount /dev/sda1
sudo ntfsfix /dev/sda1
sudo mount /dev/sda1
```

A veure què et diu.
Per cert, veig que també hauries de crear aquest enllaç per tal que l'ntfsfix et funcioni amb fsck:
```
sudo ln -s /usr/bin/ntfsfix /sbin/fsck.ntfs-3g
```

Salut!
Merci Oriolbd
Porto estona liat amb la mm***a del GRUB in el VISTA!!
començo a estar desesperat!!
aquest matí he tornat a intentar amb el SUPERGRUB que i li he dit engegar partició VISTA com que no hi ha manera massa clara de sortir de l'aplicació... no se que ha passat que he perdut el GRUB i no podia entrar per cap banda...
he entrat amb el live CD i ho he restaurat però la particio de VISTA que per la mida es la sda1 no fa rés..

aqui deixo la sortida del missatge anterior... no veig rés anormal..PERÒ EL VISTA NO ARRANCA!!se'm queda la pantalla negra com si arrenqués amb el lucid
> pere@pere-portatil:~$ sudo umount /dev/sda1
[sudo] password for pere: 
pere@pere-portatil:~$ sudo ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
pere@pere-portatil:~$ sudo mount /dev/sda1
pere@pere-portatil:~$ sudo ln -s /usr/bin/ntfsfix /sbin/fsck.ntfs-3g
pere@pere-portatil:~$ 


---

### Post by oriolsbd on 2010-05-07
Hola,

El "ntfsfix" ha processat correctament aquesta partició. Si després no t'engega el Vista, és que el problema no prové d'errors que pugui arreglar l'ntfsfix.

Per cert, acabo de recordar que, el dia que va sortir Lucid Lynx, abans de l'anunci oficial moltes webs ja anunciaven unes iso que hi havia penjades. En aquestes iso (que es van arreglar en poques hores, i ja eren correctes quan es va fer l'anunci oficial) hi havia un bug que precisament el que feia és que no es pogués engegar els sistemes operatius que ja tinguéssim instal·lats abans.

No sé si tu et vas baixar el "iso" d'Ubuntu Lucid Lynx el mateix dia que sortia, abans de l'anunci oficial (l'anunci oficial va ser cap al vespre del dia 23 d'abril). Pel que veig a MuyLinux ([http://gabuntu.wordpress.com/2010/04/29/%C2%A1alerta-ubuntu-10-04-ha-sido-retrasada-por-un-bug-en-el-grub/](http://gabuntu.wordpress.com/2010/04/29/%C2%A1alerta-ubuntu-10-04-ha-sido-retrasada-por-un-bug-en-el-grub/)). La solució és ben senzilla: fer una actualització dels paquets d'Ubuntu. És a dir:
```
sudo apt-get update
sudo apt-get upgrade
```

També ho pots fer des del Gestor d'Actualitzacions.

De tota manera, no sé si deu ser això... :-(

Salut!

---

### Post by pserra on 2010-05-07
> **oriolsbd said:**
> Hola,

El "ntfsfix" ha processat correctament aquesta partició. Si després no t'engega el Vista, és que el problema no prové d'errors que pugui arreglar l'ntfsfix.

Per cert, acabo de recordar que, el dia que va sortir Lucid Lynx, abans de l'anunci oficial moltes webs ja anunciaven unes iso que hi havia penjades. En aquestes iso (que es van arreglar en poques hores, i ja eren correctes quan es va fer l'anunci oficial) hi havia un bug que precisament el que feia és que no es pogués engegar els sistemes operatius que ja tinguéssim instal·lats abans.
Salut!
Merci per la rapida resposta, el vaig instal·lar dilluns del servidor "es"... semblava que tot havia anat perfecte fins quan vaig voler accedir a VISTA....
No tinc més alternatives??  a ningú més li ha passat?? hi ha algun remei 'xapussero' per fer 'ressucitar' el VISTA? ja que puc accedir a la seva partició des de Ubuntu..
salut!

---

### Post by pserra on 2010-05-07
Hola,
acabo de veure una incongruència que potser es la que m'esta donant els problemes....
a /media tinc les particions ```
pere@pere-portatil:/media$ ls -l
total 40
lrwxrwxrwx  1 root root     6 2009-06-26 17:35 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2009-06-26 17:35 cdrom0
drwxrwxrwx  1 root root  8192 2010-05-07 00:05 COMPARTIT
dr-xr-xr-x  1 root root 16384 2010-05-01 01:07 RECOVERY
drwxrwxrwx 20 root root  4096 2010-05-07 23:41 SMALL
drwxrwxrwx  1 root root  8192 2010-05-03 22:28 vista

```
però si vaig a computer... em surten 2 SMALLS i si vull entrar en el segon el erro em diu:
> 
NO S'HA POGUT MUNTAR SMALL
mount: /dev/sda5 ja està muntat o /media/SMALL està ocupat
mount: segons mtab, /dev/sda5 ja està muntat a /media/SMALL.

i evidentment esta a mtab:
> /dev/sda7 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda4 /media/COMPARTIT fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda2 /media/RECOVERY fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
**/dev/sda5 /media/SMALL vfat rw,noexec,nosuid,nodev,utf8,umask=000 0 0**
/dev/sda1 /media/vista fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
gvfs-fuse-daemon /home/pere/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=pere 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
com puc eliminar aquest SMALL paràsit... potser el problema de que no puc entrar al Vista pot venir per aquesta incongruència (o no)..
He probat des de nautilus.. però em diu que aquesta carpeta no hi pot entrar...
merci...

---

### Post by pserra on 2010-05-20
Aquest tema el vaig aparcar, uns dies, el vaig tornar a obrir en un altre enllaç:
                  [http://ubuntuforums.org/showthread.php?t=1486809]("http://ubuntuforums.org/showthread.php?t=1486809")
al qual wgarcia s'ha esforçat a configurar el grub... he aprés moltes coses sobre el grub.....pero al final he optat per 'formatejada' i començar de 0, i tot perfecte...
Moraleja:
    quan una cosa dona molts problemes, BORRON I CUENTA NUEVA!!

---

