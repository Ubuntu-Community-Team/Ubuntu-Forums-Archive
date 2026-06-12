---
title: "eliminat partició 'parasita'??"
date: 2010-05-08
forum: Catalan Team
---

### Post by pserra on 2010-05-08
Hola,
ahir me'n vaig donar compte i potser es el motiu del meu problema en l'engegada del windows..
ahir em vaig donar compte que si vaig a computer// tinc una partició repetida... en canvi a media/ les tinc bé..
a /media tinc les particions

>     
    pere@pere-portatil:/media$ ls -l
    total 40
    lrwxrwxrwx 1 root root 6 2009-06-26 17:35 cdrom -> cdrom0
    drwxr-xr-x 2 root root 4096 2009-06-26 17:35 cdrom0
    drwxrwxrwx 1 root root 8192 2010-05-07 00:05 COMPARTIT
    dr-xr-xr-x 1 root root 16384 2010-05-01 01:07 RECOVERY
    drwxrwxrwx 20 root root 4096 2010-05-07 23:41 SMALL
    drwxrwxrwx 1 root root 8192 2010-05-03 22:28 vista



però si vaig a computer... em surten 2 SMALLS i si vull entrar en el segon, el error em diu:

    > NO S'HA POGUT MUNTAR SMALL
    mount: /dev/sda5 ja està muntat o /media/SMALL està ocupat
    mount: segons mtab, /dev/sda5 ja està muntat a /media/SMALL



i evidentment esta a mtab:
> 
    /dev/sda7 / ext3 rw,relatime,errors=remount-ro 0 0
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
    /dev/sda2 /media/RECOVERY fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_p ermissions 0 0
    **/dev/sda5 /media/SMALL vfat rw,noexec,nosuid,nodev,utf8,umask=000 0 0**
    /dev/sda1 /media/vista fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
    gvfs-fuse-daemon /home/pere/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=pere 0 0
    binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0


com puc eliminar aquest SMALL paràsit... potser el problema de que no puc entrar al Vista pot venir per aquesta incongruència (o no)..
He probat des de nautilus.. però em diu que aquesta carpeta no hi pot entrar...
merci...

---

### Post by wgarcia on 2010-05-09
A mi em sembla que aquesta partició extra no és el causant que no puguis iniciar el Vista. Sempre la pots eliminar des del gparted des-muntant-la, reformatejant l'espai i re-assignant-lo a una altra partició, però no crec que sigui el problema. 

Fent una mica d'investigació, i per la forma en que tens les particions, una possibilitat és que el grub s'hagi instal·lat a l'espai d'arrencada del Windows Vista, i per això no pugui arrencar. 

Si pots seguir un article en anglès, mira't aquest:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

explica pas per pas com solucionar aquest problema.

---

### Post by pserra on 2010-05-09
> **wgarcia said:**
> A mi em sembla que aquesta partició extra no és el causant que no puguis iniciar el Vista. Sempre la pots eliminar des del gparted des-muntant-la, reformatejant l'espai i re-assignant-lo a una altra partició, però no crec que sigui el problema. 

Fent una mica d'investigació, i per la forma en que tens les particions, una possibilitat és que el grub s'hagi instal·lat a l'espai d'arrencada del Windows Vista, i per això no pugui arrencar. 



explica pas per pas com solucionar aquest problema.
Merci wgarcia,
demà m'ho miro... lo del Gparted no m'apareixen 2 smalls..
no se perquè a Computer Si... adjunto pantalla gparted... em queda un espai no assignat de 4 mb però no el puc borrar/reassignar...
Merci
[http://www.fotoranking.es/show.php?img=80417_gparted.png](http://www.fotoranking.es/show.php?img=80417_gparted.png)
una pregunta respecte al foro.. com s'adjunta una imatge? em pensava que era incloent l'anllaç anterior entre [img] que es el
que s'em genera.. però no ha estat així..

---

### Post by pserra on 2010-05-09
> **wgarcia said:**
> A mi em sembla que aquesta partició extra no és el causant que no puguis iniciar el Vista. Sempre la pots eliminar des del gparted des-muntant-la, reformatejant l'espai i re-assignant-lo a una altra partició, però no crec que sigui el problema. 

Fent una mica d'investigació, i per la forma en que tens les particions, una possibilitat és que el grub s'hagi instal·lat a l'espai d'arrencada del Windows Vista, i per això no pugui arrencar. 

Si pots seguir un article en anglès, mira't aquest:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

explica pas per pas com solucionar aquest problema.
hola wgarcia,
esta molt bé aquest enllaç i aquesy script passa molta informació... però el grub... no se em posa que el tinc a:
> =================== Boot Info Summary: ===========

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
miraré adjuntar arxiu sortida... però penso que potser no es aquest el problema... me'n vaig a dormir i demà ho repassarem..
Merci-

---

### Post by pserra on 2010-05-20
Al final una 'formatejada' amb el Gparted tant de ubuntu com de windows ja que no engegava, reinstal·lar des de live... i tot perfecte!! ja no apareix la partició.

---

