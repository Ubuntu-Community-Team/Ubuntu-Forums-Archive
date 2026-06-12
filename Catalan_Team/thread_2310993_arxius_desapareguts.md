---
title: "arxius desapareguts"
date: 2016-01-23
forum: Catalan Team
---

### Post by josep-maria on 2016-01-23
Tinc l'ubuntu 12.04. He volgut ficar-hi uns quants arxius (imatges, la majoria) que tenia a una memòria flash, però no els he vist, sembla que han desaparegut. Quan intento mirar el contingut de la carpeta, em diu que "hi ha hagut un error treient informació de l'arxiu...". Potser una imatge s'ha fet malbé, però per què no em deixa veure les altres?
He mirat els permisos de la carpeta que els conté, i suposo que on diu "accés al fitxer" cal que digui "lectura i escriptura". Ho he volgut canviar però no m'ha deixat.

---

### Post by wgarcia on 2016-01-25
Vols dir que no els veus a la "memòria flash", o que un cop copiats a l'ordinador a una carpeta, no els veus a aquesta carpeta de l'ordinador?

---

### Post by josep-maria on 2016-01-25
No els veig a la memòria flash. No arribo pas a poder copiar res.

---

### Post by wgarcia on 2016-01-26
Si endolles la memòria flash al port USB, es veu la carpeta corresponent i la pots obrir i mirar la llista de fitxers que n'hi ha?

---

### Post by josep-maria on 2016-01-26
Sí que veig la icona de la carpeta, però quan hi faig clic surt una finestreta que diu: "hi ha hagut un error obtenint informació de l'arxiu: (hi diu el nom de l'arxiu)".
Si tanco aquesta finestreta, veig que el contingut de la carpeta està en blanc.
A la memòria flash hi han dues carpetes més. Sí que em deixa obrir-les i fer-hi canvis. Però no em deixa obrir cap carpeta nova.
Com puc esborrar l'arxiu que diu que està malament? Potser així podria salvar els altres.

---

### Post by wgarcia on 2016-01-27
Penso que més que un arxiu corrupte, pot tractar-se del sistema de fitxers corrupte. Quin format de fitxers té, ho saps? El més probable és que tingui format "vfat", o "fat32". Aquest és un format de Windows, que òbviament els sistemes Linux poden llegir. 

Per tant primer s'hauria d'esbrinar quin sistema de fitxers té la memòria flash. Per això pots donar l'ordre:
```
mount
```
Això et mostrarà tots els discos que tens muntat i s'haurà d'identificar quin d'ells és la memòria flash, normalment /dev/sda serà el disc dur i /dev/sdb, /dev/sdc, ... identificarà altres volums (disc durs externs, memòries flash) que tinguis muntats al sistema.

---

### Post by josep-maria on 2016-01-27
Ha contestat tot això següent, però suposo que la línia que calia trobar és:
/dev/sdb1 on /media/pep/cnmemoryUSB type vfat 
I que la classe d'arxiu és vfat:


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

pep@pep-System-Product-Name:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1991324k,nr_inodes=205896,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=401568k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=21,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=401568k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdb1 on /media/pep/cnmemoryUSB type vfat (ro,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
pep@pep-System-Product-Name:~$

---

### Post by wgarcia on 2016-01-28
Pots provar de veure si es pot reparar el disc. Fes una còpia de les carpetes i fitxers que sí que puguis llegir del disc, si n'hi ha, després clica amb el botó dret a la icona de la memòria flash , clica "desmunta", i entra:

```
fsck.vfat -r /dev/sdb1
```

Si es queixa que no tens permisos suficient, a aquesta ordre posa-li "sudo" endavant.

---

### Post by josep-maria on 2016-01-29
He fet clic a la icona de la carpeta que està malament. No he vist res de "desmunta", però he fet clic a "open in terminal". Hi he escrit "sudo fsck.vfat -r /dev/sdb1".
Ha contestat aixó:

pep@pep-System-Product-Name:/media/pep/cnmemoryUSB/ficar-pc-mas$ sudo fsck.vfat -r /dev/sdb1
[sudo] password for pep: 
fsck.fat 3.0.28 (2015-05-16)
0x25: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
/ficar-pc-mas/casa-teva-vista
  Contains a free cluster (28213). Assuming EOF.
/ficar-pc-sants/.goutputstream-KKZXAY
  Contains a free cluster (28395). Assuming EOF.
/ficar-pc-sants/.goutputstream-KKZXAY
  File size is 2861 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
Reclaimed 25251 unused clusters (206856192 bytes).
Perform changes ? (y/n) y
/dev/sdb1: 98 files, 4026/61471 clusters
pep@pep-System-Product-Name:/media/pep/cnmemoryUSB/ficar-pc-mas$ 


Però segueixo sense poder esborrar la carpeta dolenta. Llavors he fet clic dret a la icona de la carpeta dolenta, i un altre clic a "open as administrator". Ara m'ha deixat veure tots els altres arxius que no podia veure. No he pogut esborrar la carpeta dolenta, però ja he pogut recuperar tots els altres arxius. Deixaré la memòria flash com a espatllada, no passa res. Moltes gràcies.

---

### Post by wgarcia on 2016-01-30
Abans de llençar la memòria flash, amb la següent ordre potser s'esborrarà la carpeta dolenta (assumint que ja has recuperat tot el que hi havia a dins):
```
sudo rm -fr /media/pep/cnmemoryUSB/ficar-pc-mas
```
ADVERTIMENT MOLT SERIÓS: Compte amb "sudo rm -fr", una de les ordres més perilloses a Linux, assegura't que el que poses a continuació és realment la carpeta que vols esborrar, perquè amb aquesta ordre i posant alguna cosa incorrecta a continuació d'ella podries carregar-te tot el sistema.

---

