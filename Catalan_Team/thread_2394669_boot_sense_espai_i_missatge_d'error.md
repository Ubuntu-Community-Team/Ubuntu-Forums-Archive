---
title: "boot sense espai i missatge d'error"
date: 2018-06-19
forum: Catalan Team
---

### Post by rvprada on 2018-06-19
Hola, em passen dues coses que suposo que tindran alguna cosa a veure.
Primer a l'encendre em deia que el boot estava ple, però en algun moment suposo que vaig acceptar i no em torna a aparèixer però si vaig a propietats em surt això:
[ATTACH=CONFIG]280153[/ATTACH]

I per una altra banda em surt una icona de prohibit a la barra de dalt amb el següent missatge:
[ATTACH=CONFIG]280154[/ATTACH]
No sé si es veu, si no, ho copio.
Moltes gràcies.
Ah, el meu ubuntu és 16.04.1 LTS

---

### Post by wgarcia on 2018-06-21
Pel tema de l'espai, es pot mirar des d'una terminal (obre-la des del "dash" o amb control-alt-t) i entrant:

```
df
```

això indicarà l'espai que usen les diferents particions.

Pel que fa al missatge d'actualitzacions, també des d'una terminal, et pot fer:

```
sudo apt update
sudo apt upgrade
```

i a veure què diu.

---

### Post by rvprada on 2018-06-25
Moltes gràcies, això és el que em diu:

df
S. fitxers                  Blocs de 1K    En ús Disponible  %Ús Muntat a
udev                            1941540        0    1941540   0% /dev
tmpfs                            392500     6232     386268   2% /run
/dev/mapper/ubuntu--vg-root   475567184 86635412  364751244  20% /
tmpfs                           1962488    13908    1948580   1% /dev/shm
tmpfs                              5120        4       5116   1% /run/lock
tmpfs                           1962488        0    1962488   0% /sys/fs/cgroup
/dev/loop1                        93056    93056          0 100% /snap/krop/104
/dev/loop6                        75264    75264          0 100% /snap/remmina/1096
/dev/loop7                        78464    78464          0 100% /snap/remmina/600
/dev/loop5                        75264    75264          0 100% /snap/remmina/766
/dev/loop8                        93056    93056          0 100% /snap/krop/65
/dev/loop2                        93056    93056          0 100% /snap/krop/61
/dev/loop0                        88704    88704          0 100% /snap/core/4571
/dev/loop3                        88704    88704          0 100% /snap/core/4650
/dev/loop4                        89088    89088          0 100% /snap/core/4830
/dev/sda2                        483946   473478          0 100% /boot
/dev/sda1                        523248     3480     519768   1% /boot/efi
tmpfs                            392500      124     392376   1% /run/user/1000

sudo apt update
[sudo] contrasenya per a ramiro: 
Obj:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Obj:2 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial InRelease                     
Obj:3 [http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu](http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu) xenial InRelease
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Obj:5 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                           
Obj:6 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Obj:7 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Ign:8 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease               
Obj:9 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release     
Obj:10 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release
S'està llegint la llista de paquets&#8230; Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
229 packages can be upgraded. Run 'apt list --upgradable' to see them.

udo apt upgrade
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
Potser voldreu executar «apt-get -f install» per a corregir-ho.
Els següents paquets tenen dependències sense satisfer:
 linux-image-extra-4.4.0-127-generic : Depèn: linux-image-4.4.0-127-generic però no està insta&#320;lat
 linux-image-extra-4.4.0-128-generic : Depèn: linux-image-4.4.0-128-generic però no està insta&#320;lat
 linux-image-generic : Depèn: linux-image-4.4.0-128-generic però no està insta&#320;lat
 linux-signed-image-4.4.0-127-generic : Depèn: linux-image-4.4.0-127-generic (= 4.4.0-127.153) però no està insta&#320;lat
 linux-signed-image-4.4.0-128-generic : Depèn: linux-image-4.4.0-128-generic (= 4.4.0-128.154) però no està insta&#320;lat
E: Dependències sense satisfer. Proveu-ho emprant -f.

---

### Post by wgarcia on 2018-06-26
Sembla que els dos problemes estan relacionats. La partició "/boot" mostra 100% d'ús, per tant no et deixa actualitzar el nucli (kernel) i això és del que es queixen les actualitzacions. 

Es podria primer provar d'eliminar nuclis antics. Prova de fer:

```
sudo apt autoremove
```

Això t'hauria de deixar amb els últims nuclis i hauria d'eliminar nuclis molt antics.

---

### Post by rvprada on 2018-06-27
**Em diu això:**
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
Potser voldreu executar «apt-get -f install» per a corregir-ho.
Els següents paquets tenen dependències sense satisfer:
 linux-image-extra-4.4.0-127-generic : Depèn: linux-image-4.4.0-127-generic però no està insta&#320;lat
 linux-image-extra-4.4.0-128-generic : Depèn: linux-image-4.4.0-128-generic però no està insta&#320;lat
 linux-image-generic : Depèn: linux-image-4.4.0-128-generic però no està insta&#320;lat
 linux-signed-image-4.4.0-127-generic : Depèn: linux-image-4.4.0-127-generic (= 4.4.0-127.153) però no està insta&#320;lat
 linux-signed-image-4.4.0-128-generic : Depèn: linux-image-4.4.0-128-generic (= 4.4.0-128.154) però no està insta&#320;lat
E: Dependències sense satisfer. Proveu-ho emprant -f.

[B]He fet:
sudo apt-get -f install[/B]
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
S'estan corregint les dependències&#8230; Fet
Els paquets següents s'han insta&#320;lat automàticament i ja no són necessaris:
  libqpdf17 linux-headers-4.4.0-101 linux-headers-4.4.0-101-generic
  linux-headers-4.4.0-116 linux-headers-4.4.0-116-generic
  linux-headers-4.4.0-119 linux-headers-4.4.0-119-generic
  linux-headers-4.4.0-127 linux-headers-4.4.0-127-generic
  linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic linux-headers-4.4.0-96
  linux-headers-4.4.0-96-generic linux-headers-4.4.0-98
  linux-headers-4.4.0-98-generic linux-image-4.4.0-101-generic
  linux-image-4.4.0-116-generic linux-image-4.4.0-119-generic
  linux-image-4.4.0-127-generic linux-image-4.4.0-93-generic
  linux-image-4.4.0-96-generic linux-image-4.4.0-98-generic
  linux-image-extra-4.4.0-101-generic linux-image-extra-4.4.0-116-generic
  linux-image-extra-4.4.0-119-generic linux-image-extra-4.4.0-127-generic
  linux-image-extra-4.4.0-93-generic linux-image-extra-4.4.0-96-generic
  linux-image-extra-4.4.0-98-generic linux-signed-image-4.4.0-101-generic
  linux-signed-image-4.4.0-116-generic linux-signed-image-4.4.0-119-generic
  linux-signed-image-4.4.0-127-generic linux-signed-image-4.4.0-93-generic
  linux-signed-image-4.4.0-96-generic linux-signed-image-4.4.0-98-generic
  python-appindicator python-gobject python-mygpoclient python-simplejson
Empreu «sudo apt autoremove» per a suprimir-los.
The following additional packages will be installed:
  linux-image-4.4.0-127-generic linux-image-4.4.0-128-generic
Paquets suggerits:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
S'insta&#320;laran els paquets NOUS següents:
  linux-image-4.4.0-127-generic linux-image-4.4.0-128-generic
0 actualitzats, 2 nous a insta&#320;lar, 0 a suprimir i 231 no actualitzats.
11 no insta&#320;lats o suprimits completament.
S'ha d'obtenir 0 B/44,2 MB d'arxius.
Després d'aquesta operació s'empraran 136 MB d'espai en disc addicional.
Voleu continuar? [S/n] s
(S'està llegint la base de dades&#8230; hi ha 543604 fitxers i directoris instal·lats actualment.)
S'està preparant per a desempaquetar &#8230;/linux-image-4.4.0-128-generic_4.4.0-128.154_amd64.deb&#8230;
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-128-generic /boot/vmlinuz-4.4.0-128-generic
Done.
S'està desempaquetant linux-image-4.4.0-128-generic (4.4.0-128.154)&#8230;
dpkg: s'ha produït un error en processar l'arxiu /var/cache/apt/archives/linux-image-4.4.0-128-generic_4.4.0-128.154_amd64.deb (--unpack):
 no es poden copiar les dades extretes de «./boot/System.map-4.4.0-128-generic» a «/boot/System.map-4.4.0-128-generic.dpkg-new»: no s'ha pogut escriure (No resta espai al dispositiu)
No s'ha escrit cap informe perquè el missatge d'error indica una fallida per disc ple
     dpkg-deb: s'ha produït un error: el subprocés enganxa ha estat finalitzat pel senyal (La canonada s&#8217;ha trencat)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-128-generic /boot/vmlinuz-4.4.0-128-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-128-generic /boot/vmlinuz-4.4.0-128-generic
S'està preparant per a desempaquetar &#8230;/linux-image-4.4.0-127-generic_4.4.0-127.153_amd64.deb&#8230;
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-127-generic /boot/vmlinuz-4.4.0-127-generic
Done.
S'està desempaquetant linux-image-4.4.0-127-generic (4.4.0-127.153)&#8230;
dpkg: s'ha produït un error en processar l'arxiu /var/cache/apt/archives/linux-image-4.4.0-127-generic_4.4.0-127.153_amd64.deb (--unpack):
 no es poden copiar les dades extretes de «./boot/vmlinuz-4.4.0-127-generic» a «/boot/vmlinuz-4.4.0-127-generic.dpkg-new»: no s'ha pogut escriure (No resta espai al dispositiu)
No s'ha escrit cap informe perquè el missatge d'error indica una fallida per disc ple
     dpkg-deb: s'ha produït un error: el subprocés enganxa ha estat finalitzat pel senyal (La canonada s&#8217;ha trencat)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-127-generic /boot/vmlinuz-4.4.0-127-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-127-generic /boot/vmlinuz-4.4.0-127-generic
S'han trobat errors en processar:
 /var/cache/apt/archives/linux-image-4.4.0-128-generic_4.4.0-128.154_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-127-generic_4.4.0-127.153_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

**He tornat a fer sudo apt autoremove i em torna a sortir el mateix.**

---

### Post by wgarcia on 2018-06-28
L'ordre

```
sudo apt-get -f install
```

no funciona per la manca d'espai a la partició /boot. Potser el que es pot fer és fer una llista dels nuclis instal·lats i eliminar els antics. Per fer una llista dels nuclis instal·lats excloent el que s'està executant, aquesta ordre hauria de ser útil

```
 dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r) | grep ii 
```

i després s'hauria de fer també

```
uname -a
```
per assegurar-se quin és el nucli que s'està executant.

Un cop determinat els vells, es podran eliminar per fer espai a /boot.

---

### Post by rvprada on 2018-06-28
[B]Ho sento però un cop fet això què has dit no tinc ni idea de com fer això que dius d'eliminar els antics. Això és el que em. diu. Moltíssimes gràcies.

dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r) | grep ii[/B]
ii  linux-image-4.4.0-101-generic               4.4.0-101.124                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-116-generic               4.4.0-116.140                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-119-generic               4.4.0-119.143                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-121-generic               4.4.0-121.145                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-93-generic                4.4.0-93.116                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-96-generic                4.4.0-96.119                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-98-generic                4.4.0-98.121                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP

**uname -a**
Linux ramiro-Lenovo-B50-10 4.4.0-124-generic #148-Ubuntu SMP Wed May 2 13:00:18 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

**No sé si t'és útil, però això és el que hi ha a boot:**
/boot/efi
/boot/grub
/boot/abi-4.4.0-93-generic
/boot/abi-4.4.0-96-generic
/boot/abi-4.4.0-98-generic
/boot/abi-4.4.0-101-generic
/boot/abi-4.4.0-116-generic
/boot/abi-4.4.0-119-generic
/boot/abi-4.4.0-121-generic
/boot/abi-4.4.0-124-generic
/boot/config-4.4.0-93-generic
/boot/config-4.4.0-96-generic
/boot/config-4.4.0-98-generic
/boot/config-4.4.0-101-generic
/boot/config-4.4.0-116-generic
/boot/config-4.4.0-119-generic
/boot/config-4.4.0-121-generic
/boot/config-4.4.0-124-generic
/boot/initrd.img-4.4.0-93-generic
/boot/initrd.img-4.4.0-96-generic
/boot/initrd.img-4.4.0-98-generic
/boot/initrd.img-4.4.0-101-generic
/boot/initrd.img-4.4.0-116-generic
/boot/initrd.img-4.4.0-119-generic
/boot/initrd.img-4.4.0-121-generic
/boot/initrd.img-4.4.0-124-generic
/boot/memtest86+.bin
/boot/memtest86+.elf
/boot/memtest86+_multiboot.bin
/boot/retpoline-4.4.0-116-generic
/boot/retpoline-4.4.0-119-generic
/boot/retpoline-4.4.0-121-generic
/boot/retpoline-4.4.0-124-generic
/boot/System.map-4.4.0-93-generic
/boot/System.map-4.4.0-96-generic
/boot/System.map-4.4.0-98-generic
/boot/System.map-4.4.0-101-generic
/boot/System.map-4.4.0-116-generic
/boot/System.map-4.4.0-119-generic
/boot/System.map-4.4.0-121-generic
/boot/System.map-4.4.0-124-generic
/boot/vmlinuz-4.4.0-93-generic
/boot/vmlinuz-4.4.0-93-generic.efi.signed
/boot/vmlinuz-4.4.0-96-generic
/boot/vmlinuz-4.4.0-96-generic.efi.signed
/boot/vmlinuz-4.4.0-98-generic
/boot/vmlinuz-4.4.0-98-generic.efi.signed
/boot/vmlinuz-4.4.0-101-generic
/boot/vmlinuz-4.4.0-101-generic.efi.signed
/boot/vmlinuz-4.4.0-116-generic
/boot/vmlinuz-4.4.0-116-generic.efi.signed
/boot/vmlinuz-4.4.0-119-generic
/boot/vmlinuz-4.4.0-119-generic.efi.signed
/boot/vmlinuz-4.4.0-121-generic
/boot/vmlinuz-4.4.0-121-generic.efi.signed
/boot/vmlinuz-4.4.0-124-generic
/boot/vmlinuz-4.4.0-124-generic.efi.signed

---

### Post by wgarcia on 2018-06-29
D'acord, s'haurien d'eliminar tots els nuclis antics i deixar sols l'últim i el penúltim. Com es veu a la primera sortida, hi ha un munt de nuclis antics i per això s'ha omplert la partició /boot. S'haurien d'eliminar tots menys el 124 que és el que s'està usant i el 121 que és l'anterior. Es pot començar pel més antic de tots:

```
sudo apt remove  linux-image-4.4.0-101-generic  linux-headers-4.4.0-101-generic
```

A veure si funciona això, si funciona després es podrà eliminar la resta de nuclis antics.

---

### Post by rvprada on 2018-06-30
Em sap greu seguir donant tant la tabarra, però torna a respondre el mateix:
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
Potser voldreu executar «apt-get -f install» per corregir-ho:
Els següents paquets tenen dependències sense satisfer:
 linux-image-extra-4.4.0-127-generic : Depèn: linux-image-4.4.0-127-generic però no serà insta&#320;lat
 linux-image-extra-4.4.0-128-generic : Depèn: linux-image-4.4.0-128-generic però no serà insta&#320;lat
 linux-image-extra-4.4.0-93-generic : Depèn: linux-image-4.4.0-93-generic però no serà insta&#320;lat
 linux-image-generic : Depèn: linux-image-4.4.0-128-generic però no serà insta&#320;lat
 linux-signed-image-4.4.0-127-generic : Depèn: linux-image-4.4.0-127-generic (= 4.4.0-127.153) però no serà insta&#320;lat
 linux-signed-image-4.4.0-128-generic : Depèn: linux-image-4.4.0-128-generic (= 4.4.0-128.154) però no serà insta&#320;lat
 linux-signed-image-4.4.0-93-generic : Depèn: linux-image-4.4.0-93-generic (= 4.4.0-93.116) però no serà insta&#320;lat
E: Dependències insatisfetes. Proveu amb «apt-get -f install» sense paquets (o especifiqueu una solució).

**Seria una barbaritat eliminar-los un a un amb compte a través de l'explorador en lloc de des d'un terminal?**
Infinites gràcies.

---

### Post by wgarcia on 2018-07-02
Doncs s'haurà de força la desinstal·lació amb "dpkg" en comptes de "sudo apt remove". Això és vàlid en aquest cas que hi ha les dependències sense satisfer, però no s'hauria d'usar de forma general per eliminar paquets. Per tant ara s'ha de provar:

```
sudo dpkg --force-all -P linux-image-4.4.0-101-generic
sudo dpkg --force-all -P linux-headers-4.4.0-101-generic
```

a veure si hi ha sort així.

Jo no eliminaria els fitxers de la carpeta "/boot" directament, això pot afectar l'arrencada del sistema i crear més problemes.

---

### Post by rvprada on 2018-07-02
Hola, ha funcionat.

He fet 
sudo dpkg --force-all -P linux-image-4.4.0-101-generic
sudo dpkg --force-all -P linux-headers-4.4.0-101-generic

per als paquets antics.

He fet update i upgrade i em seguia dient lo de Proveu-ho emprant -f.

He fet sudo apt-get -f install i em seguia donant errors per la manca d'espai, és com si no ho hagués eliminat tot.
Llavors he vist que ja em deixava fer sudo apt remove  linux-image-4.4.0-101-generic  linux-headers-4.4.0-101-generic. I ho he fet per a tots els nuclis antics excepte els dos últims que ara són el 128 i el 130.
En els primers em donava errors però als darrers ja no, i m'anava recordant que m'havien quedat coses dels primer i que fes autoremove.
He fet autoremove, i sembla que ha tret coses sueltes que havien quedat.
Llavors he fet update i upgrade i ho ha fet sense cap problema.
Ja no em surt el missatge d'error. M'imagino que ja està tot bé.
Moltes gràcies wgarcia, és una passada la feina que fas, moltíssimes gràcies, de veritat.

---

