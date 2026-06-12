---
title: "instal·lat alternate 12.04 -&gt; pèrdua accés Windows 7"
date: 2012-10-13
forum: Catalan Team
---

### Post by jinglada on 2012-10-13
Obro nou fil per a separar problemes. 
L'anterior és aquest [http://ubuntuforums.org/showthread.php?t=2069283](http://ubuntuforums.org/showthread.php?t=2069283)

[albandy]("http://ubuntuforums.org/member.php?u=715896") em digué que fes el següent:

----------------------------------
joan@ubuntu:~$ sudo fdisk -l
[sudo] password for joan:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb1da1eb9

Dispositiu Arrenc. Inici Final Blocs Id Sistema
/dev/sda1 63 25173854 12586896 27 Hidden NTFS WinRE
/dev/sda2 * 25173855 25382699 104422+ 7 HPFS/NTFS/exFAT
/dev/sda3 25382700 262939827 118778564 7 HPFS/NTFS/exFAT
/dev/sda4 262940670 361377791 49218561 5 Estesa
/dev/sda5 262940672 298876927 17968128 83 Linux
/dev/sda6 298878976 361377791 31249408 82 Intercanvi Linux / Solaris
joan@ubuntu:~$

---------------------------

en seleccionar el loader de W en el grub

> menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root FCCCB71CCCB6D05E
	chainloader +1
}

em surt el següent missatge,

> No se puede iniciar windows. Es posible que un cambio de hardware o de sofware reciente sea la causa. para corregir el problema:

1.-inserte el disco de instalacion de windows y reinicie el equipo.
2.-elija la configuracion de idioma y despues haga clic en siguiente
3.-haga clic en reparar equipo

si no tiene este disco, pongase en contacto con el administrador del sistema o con el fabricante del equipo para obtener ayuda:

Estado: 0xc000000f
informacion: Error al seleccionar el arranque, no se puede tener acceso a un dispositivo requerido

No tinc el disc d'instalació de windows perquè no venia en aquest portàtil comprat a la cadena "Confort".

Agrairia ajuda ja que el portàtil és del meu gendre i ja fa tres dies que no el pot fer servir :-(

---

### Post by wgarcia on 2012-10-13
En el menú del grub no tens una opció de "Recuperació de windows" o una cosa així? En aquest cas l'estratègia seria escollir aquesta opció, deixar que es recuperi Windows, i això faria que no veiessis més l'Ubuntu però encara estaria al disc. Per recuperar l'accés a Ubuntu s'hauria de començar el sistema amb un USB o CD autònom ("live") i reinstal·lar el grub al MBR del disc (Master Boot Record, el sector d'arrencada del disc), ja veuríem com es fa això si fa falta.

Però tot això seria possible si hi ha aquesta partició de recuperació de Windows. Té morbo la cosa, que et venguin un ordinador, et cobrin pel sistema operatiu, però no et donin res, ni que fos almenys un enllaç on poder-te baixar el sistema operatiu si tens algun problema.

---

### Post by jinglada on 2012-10-13
> **wgarcia said:**
> En el menú del grub no tens una opció de "Recuperació de windows" o una cosa així? En aquest cas l'estratègia seria escollir aquesta opció, deixar que es recuperi Windows, i això faria que no veiessis més l'Ubuntu però encara estaria al disc. Per recuperar l'accés a Ubuntu s'hauria de començar el sistema amb un USB o CD autònom ("live") i reinstal·lar el grub al MBR del disc (Master Boot Record, el sector d'arrencada del disc), ja veuríem com es fa això si fa falta.

Gràcies wgarcia. Si que hi ha l'entrada de menú que dius i de fet ja la vaig executar i em van sortir alguns misatges i el logo del Windows, dient que s'executava el Windows i al final es va quedar molta estona amb una pantalla que deia:
"Packard Bell Recovery Management"
"Please wait a moment"
i un petit cercle que rodava, fins que al cap de mitja hora el vaig parar amb l'interruptor.

Ara l'he tornat a engegar i s'ha quedat en aquesta situació. 

Quant temps et sembla que l'he de deixar?

> Però tot això seria possible si hi ha aquesta partició de recuperació de Windows. Té morbo la cosa, que et venguin un ordinador, et cobrin pel sistema operatiu, però no et donin res, ni que fos almenys un enllaç on poder-te baixar el sistema operatiu si tens algun problema.

Quan la meva filla va demanar el disc li van dir que era una oferta i que ja venia així. 

A la banda de sota del portàtil hi ha una etiqueta amb les dades dela llicència Windows. Que et sembla si escric a Packard Bell, els explico el cas i demano assistència per a solucionar el tema?

---

### Post by wgarcia on 2012-10-14
Respecte a la recuperació de Windows, no sé quant de temps s'ha d'esperar, no té pinta que estigui fent res si queda així sense recuperar. 

Però penso que sí que es pot demanar assistència, perquè se suposa que aquesta partició és justament per això, per recuperar el sistema per si passa alguna cosa. Si no ho fa hi ha alguna cosa que no està funcionant.

---

### Post by jinglada on 2012-10-14
> **wgarcia said:**
> Respecte a la recuperació de Windows, no sé quant de temps s'ha d'esperar, no té pinta que estigui fent res si queda així sense recuperar. 

El vaig tenir 2 hores i no es va moure.

> Però penso que sí que es pot demanar assistència, perquè se suposa que aquesta partició és justament per això, per recuperar el sistema per si passa alguna cosa. Si no ho fa hi ha alguna cosa que no està funcionant.

Et refereixes a la /dev/sda1 63 25173854 12586896 27 Hidden NTFS WinRE, oi? L'entrada corresponent del /boot/grub/grub.cfg és correcta: 

> menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root DA8CB6C38CB69989
    drivemap -s (hd0) ${root}
    chainloader +1
}

Ja he fet la consulta i diuen que en 24 hores em contestaran.

Gràcies i bon diumenge!

---

### Post by jinglada on 2012-10-17
> **wgarcia said:**
> Però penso que sí que es pot demanar assistència, perquè se suposa que aquesta partició és justament per això, per recuperar el sistema per si passa alguna cosa. Si no ho fa hi ha alguna cosa que no està funcionant.

ACER-Packard Bell em va donar un video de recuperació [http://www.youtube.com/embed/pmVT0Z9r6_Q](http://www.youtube.com/embed/pmVT0Z9r6_Q)
que no ha funcionat. Llavors m'han dit que tenen un kit de recuperació de 60,5&#8364; (IVA i ports inclosos). Han afegit que comprovi la integritat del disc perquè en cas d'avaria o sectors defectuosos la compra del kit seria innecessària.

En el fòrum en castellà m'han dit que la instal·lació d'Ubuntu sobre W7 elimina el MBR i que s'ha de tornar a instal·lar. Diuen que es pot intentar amb el Super Grup 2 perquè llavors no havia sortit aquesta versió del Super Grup (deu ser Grub, oi?). És això: [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) ?

Potser hauria de fer això?

sudo update-grub2
sudo grub-install /dev/sda

-----------------------------------
afegeixo enllaços sobre això:
-----------------------------------

[http://conocimientoadictivo.blogspot.com/2011/10/mbr-regenerator-elimina-activadores.html](http://conocimientoadictivo.blogspot.com/2011/10/mbr-regenerator-elimina-activadores.html)
[http://www.taringa.net/posts/linux/13670476/Borrar-distros-del-disco-y-reparar-MBR-de-Windows-7.html](http://www.taringa.net/posts/linux/13670476/Borrar-distros-del-disco-y-reparar-MBR-de-Windows-7.html)
[http://www.taringa.net/posts/linux/13358068/Recuperar-arranque-windows-7-_Grub-Rescue_.html](http://www.taringa.net/posts/linux/13358068/Recuperar-arranque-windows-7-_Grub-Rescue_.html)
[http://mundoeddix.blogspot.com.es/2010/06/reparar-el-mbr-de-windows-7-despues-de.html](http://mundoeddix.blogspot.com.es/2010/06/reparar-el-mbr-de-windows-7-despues-de.html)
[Windows 7 elimina MBR | Ubuntu-es]("http://www.ubuntu-es.org/node/134219#.UH7EFxKP8xA")

------------------------------------
he intentat muntar dos dispositius que m'apareixen a la carpeta d'usuari (les particions de windows?) i solament puc veure aquesta:
joan@ubuntu:/media/SYSTEM RESERVED$ ls -la
total 387
drwx------ 1 joan joan   4096 jul  3  2011 .
drwxr-xr-x 4 root root   4096 oct 18 17:39 ..
drwx------ 1 joan joan   4096 jul  3  2011 Boot
-rw------- 1 joan joan 383786 nov 20  2010 bootmgr
drwx------ 1 joan joan      0 des 29  2010 System Volume Information
joan@ubuntu:/media/SYSTEM RESERVED$ 

i amb data posterior a la instal·lació d'ubuntu hi ha:

joan@ubuntu:/media/SYSTEM RESERVED/Boot$ ls -lat
total 600
-rw------- 1 joan joan  28672 oct 18 12:56 BCD
-rw------- 1 joan joan  25600 oct 18 12:56 BCD.LOG
que no els puc llegir
--------------------------------------
l'altre diu:

No s'ha pogut muntar Packard Bell:
Error mounting: mount exited with exit code 13: Failed to load runlist for $MFT/$DATA.
highest_vcn = 0x70, last_vcn - 1 = 0x15fff
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
----------------------------

Hi ha alguna manera de recuperar algun dels directoris de dades del windows des de l'ubuntu?

---

### Post by jinglada on 2012-10-21
He reinstal · lat Ubuntu 12.04 usant tot el HD. Si la família no s'adapta reinstalaré W7 i provaré l'Ubuntu 10.04 a veure si no es càrrega l'accés al W7 com ha fet el 12.04. En instal · lar Ubuntu 12.04 usant tot el disc no hi ha hagut cap problema d'accés.

Gràcies a tots els que heu intentat ajudar-me.

---

