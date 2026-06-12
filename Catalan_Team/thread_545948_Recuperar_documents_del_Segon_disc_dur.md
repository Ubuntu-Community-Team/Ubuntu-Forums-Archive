---
title: "Recuperar documents del Segon disc dur"
date: 2007-09-08
forum: Catalan Team
---

### Post by ogmius on 2007-09-08
Hola a tots, Primer de tot una salutació i moltes gràcies... 

Després de les vacances d'estiu torno amb esperit experimentador, però... m'ha sorgit un problema:  He instal.lat a casa el Linux Mint, una sub-distro basada en Ubuntu. Tinc dos discos durs, en un dels quals he instal·lat tot el sistema de **Linux Mint**. En l'altre tenia tota una col·lecció de documents creats des de Windows: de text, videos de la mula, arxius de música, etc. 

Després d'instal·lar Linux Mint, tot ha anat com una seda, però no puc accedir als arxius que tenia anteriorment en aquest disc dur, apareix com si estigués buit. Si obro aquest disc (hdb2), apareix l'usuari root com propietari, i el volum està muntat, però no apareix cap dels documents que jo tenia prèviament. Crec que el volum està muntat en el sistema d'arxius vfat-FAT32. Si obro el ntfs-config, tan sols m'apareix l'opció **"Activar suport d'escriptura de dispositius externs**", que està activat, però no aconsegueixo cap avanç. 

La sortida de l'ordre **mount** es la següent:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hdb2 on /media/fat32 type vfat (rw,gid=1000,umask=0007,fmask=0117,utf8 )
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
fusesmb on /home/casa/Network type fuse (rw,nosuid,nodev,allow_other,max_read=32768 )

Podré recuperar tots els documents que tinc en hdb2?? 

**Moltes gràcies per avançat!!!**

---

