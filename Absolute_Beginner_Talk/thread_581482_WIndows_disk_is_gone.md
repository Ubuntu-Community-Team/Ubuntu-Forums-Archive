---
title: "WIndows disk is gone?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-10-19
It is on in nautilus.. my fstab file says this?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=72ad26b5-e137-48b6-9fdb-410331e967a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C67868FE7868EE9D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=4b090ccf-b37c-4182-9a6d-90a3610cff86 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Does anybody know how i can get it back.. it was there before :|

---

### Post by Pumalite on 2007-10-19
What do you mean, it's gone? Can you give more details?.

---

### Post by mikeyphi on 2007-10-19
SDA1 looks as though you've only got ntfs installed - check/install ntfs-3g

---

### Post by mech7 on 2007-10-19
it says:

chris@chris-laptop:~$ check/install ntfs-3g
bash: check/install: No such file or directory

---

### Post by Pumalite on 2007-10-19
sudo apt-get install ntfs-3g

---

### Post by mech7 on 2007-10-19
doesnt work :(

chris@chris-laptop:~$ sudo apt-get install ntfs-3g
[sudo] password for chris:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@chris-laptop:~$ check/install ntfs-3g
bash: check/install: No such file or directory

---

### Post by andrewsomething on 2007-10-19
> **mech7 said:**
> It is on in nautilus.. my fstab file says this?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=72ad26b5-e137-48b6-9fdb-410331e967a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C67868FE7868EE9D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=4b090ccf-b37c-4182-9a6d-90a3610cff86 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Does anybody know how i can get it back.. it was there before :|

Could you please try to be a bit more specific about your problem? It will help us help you... :)

Do you mean that you can't access your Windows drive from Ubuntu or that you can't boot into Windows? 

What steps did you take before your problem occurred?

---

### Post by mech7 on 2007-10-19
> **andrewsomething said:**
> Could you please try to be a bit more specific about your problem? It will help us help you... :)

Do you mean that you can't access your Windows drive from Ubuntu or that you can't boot into Windows? 

What steps did you take before your problem occurred?

Well it means i had an icon with my windows disk.. and suddenly it is gone :confused:

---

### Post by Pumalite on 2007-10-19
Look in /media

---

### Post by mech7 on 2007-10-19
/media/sda1

Is empty :(

---

### Post by BOZG on 2007-10-19
Did you shutdown Windows properly?

Try rebooting Windows and making sure that it's shutdown naturally.

My hda1 disappeared recently because I hadn't shutdown Windows properly.

---

### Post by mech7 on 2007-11-06
> **BOZG said:**
> Did you shutdown Windows properly?

Try rebooting Windows and making sure that it's shutdown naturally.

My hda1 disappeared recently because I hadn't shutdown Windows properly.

I always hibernate never shutdown pc.. ? could this be the reason ?

---

### Post by mech7 on 2007-11-06
Btw i reinstalled it and still same problem only now:

> 
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


> 
chris@chris-laptop:~$ check/install ntfs-3g
bash: check/install: No such file or directory


---

### Post by travis31 on 2007-11-06
> **mech7 said:**
> I always hibernate never shutdown pc.. ? could this be the reason ?

Yes. Ubuntu will not mount a hibernated windows partition, shutdown windows properly and try again.

---

