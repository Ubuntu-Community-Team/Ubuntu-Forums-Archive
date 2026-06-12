---
title: "Disk bloopers"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by RolandB on 2007-07-15
OK.....not entirely new to computers and stuff but managed too  totally loose my Windows
partition.  It doesn't show in ubuntu and not when booting (anymore).
I downloaded testdisk.....unpacked it and then what????? Clicking on the icon doesn't
do anything....wrong version?  

Please help!

Roland

---

### Post by Pragmatist on 2007-07-15
If you can get into Ubuntu, and you know how to use a terminal, then try this:

```
mount
``` 


```
cat /boot/grub/menu.lst >>output
```
the l in .lst is a lowercase L  This command will generate a file called "output".  Attach that file on your next post.

---

### Post by RolandB on 2007-07-15
Thnx...maar geen output file?  Zie hieronder: 

roland@roland-desktop:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdc1 on /media/LACIE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/scd1 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=roland)
roland@roland-desktop:~$ cat /boot/grub/menu.lst >>output
roland@roland-desktop:~$

---

### Post by Pragmatist on 2007-07-15
/> dev/sdc1 on /media/LACIE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,uma  sk=077)
Is that your windows partition?
```
ls /media/LACIE
```

You need to attach the file called "output" here so we can see it.

---

### Post by RolandB on 2007-07-16
Nope sorry, backup drive...outputfile zal ik nog ns proberen met de commando's hierboven..

bedankt zover..

Roland

---

### Post by Pragmatist on 2007-07-16
> **RolandB said:**
> outputfile zal ik nog ns proberen met de commando's hierboven..

bedankt zover..

Roland

I am sorry, I only understand English.

---

### Post by splintercellguy on 2007-07-16
How about sudo fdisk -l?

---

