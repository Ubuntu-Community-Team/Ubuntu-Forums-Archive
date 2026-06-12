---
title: "new to linux - does not recognize cdrom drive"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by dileepk on 2006-12-16
i loaded 6.10 via cdrom but the system does not recognize cdrom - i can't even open it.  any ideas why - this is frustrating

---

### Post by po0f on 2006-12-16
dileepk,

You're going to have to give us more information to go on.  These are some possible scenarios:

Did you already install Ubuntu and can't get a CD mounted?  If so, post your /etc/fstab.

Or is the computer not booting the CD you burned?  If this is the case, make sure your BIOS is set to boot from CD.  Another problem could be the way you burned your CD: make sure you burned your ISO image as an ISO CD and *not* data CD.

---

### Post by dileepk on 2006-12-16
I was able to boot from CDROM.  here is the output of /etc/fstab

 dileep@dileep-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b6dfca0-6995-4c18-8d7e-658640432a17 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c8fce651-630a-48d2-b828-781c28714d59 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
dileep@dileep-laptop:~$ 


please help!

---

### Post by po0f on 2006-12-16
dileepk,

Post the output of:
```
[FONT="Courier New"]$ ls -l /dev | grep cdrom[/FONT]
```

And please clarify: did you install Ubuntu already, or are you posting this info from the live CD?

---

### Post by ciscosurfer on 2006-12-16
> **po0f said:**
> dileepk,

Post the output of:
```
[FONT=Courier New]$ ls -l /dev | grep cdrom[/FONT]
```And please clarify: did you install Ubuntu already, or are you posting this info from the live CD?I believe he's installed it...look at his username/hostname in his terminal output.

EDIT: if he hasn't modified his fstab, then cdrom should point to scd0, right?

---

### Post by ciscosurfer on 2006-12-16
> **dileepk said:**
> I was able to boot from CDROM.  here is the output of /etc/fstab

 dileep@dileep-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b6dfca0-6995-4c18-8d7e-658640432a17 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c8fce651-630a-48d2-b828-781c28714d59 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
dileep@dileep-laptop:~$ 


please help!Are you using an external SCSI CD-ROM drive?

---

### Post by dileepk on 2006-12-16
I have installed ubuntu 6.10 desktop - not posting from live CD.  i have IDE master CD and DVD writer -- this is not external SCSI CD/DVD.   Only thing i am baffled by is that CDROM was working during the ISO install of ubuntu.  I have not modified fstab.

there is no ouput from command below.

dileep@dileep-laptop:~$ ls -l /dev | grep cdrom
dileep@dileep-laptop:~$ 

please help!!!

---

### Post by dileepk on 2006-12-17
Am I missing some driver - or can I edit fstab or mtab?   This is very frustrating..   Please help!!!](*,)

---

