---
title: "[SOLVED] Partitioning"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2008-03-30
I want to create a seperate partition for "/" "usr" and "/home"

How much is recommended for the "/" partition?

I already have an idea of how much I want to use for "/usr" and "/home"

---

### Post by prshah on 2008-03-30
> **piratesmack said:**
> I want to create a seperate partition for "/" "usr" and "/home"

How much is recommended for the "/" partition?

I already have an idea of how much I want to use for "/usr" and "/home"

Simple version: 
one "/" partition, 10~15gb in size
1 swap partition 1Gb~2Gb in size
everything else "/home"

Complex version: (Not recommended)

Ideal partitioning tips:
/- Root file system. Should just contain /bin, /sbin, /dev, /root,       /lib and /etc.
Min: 100Mb	Max: 100Mb
---	---	---
/usr- Programmes and source code. 
Min: 300Mb	Max: 2Gb+
---	---	---
/var-Variable data, such as spools, man pages, news and mail        queues, database data.
Min: 400Mb	Max: 400Mb+
---	---	---
/boot-Boot kernels
Min: 20Mb	Max: 20Mb
(recommended 1st primary partition)
---	---	---
/home-User data and "stuff".
Size depends on estimated size of user data.
Min: 50Mb(?)	Max:Anything
---	---	---
/tmp-Temporary file locations
Size depends on usage. Eg. scanning of large files, etc.
---	---	---
Recommended additional partitions:
/usr/local- Ideal place to install 3rd party software
---	---	---
/var/spool/squid- recommended if proxy server
---	---	---
/var/log- recommended since log if partitioning fills up, only logging will be stopped, with no effect to rest of the system.
--	--	--
Recommended to have swap partition in the "physical" centre of the HDD.

Hope this helps and doesn't confuse.

---

### Post by Oldsoldier2003 on 2008-03-30
dont use a separate /boot partition if you plan on running different distributions. Fedora for one is one that will break everything if you share its boot partition with Ubuntu...

---

### Post by rajaram_s on 2008-03-30
isnt a /boot parition useful for recovering grub if its lost? I had the same kind of problem. I tried installin fedora on my comp which had ubuntu and vista in it. Is it possible to recovermy ubuntu? The fedora boot loader just shows fedora and vista in it... I gave a seperate /boot partition durin the installation of ubuntu but not during the installation of fedora.

---

### Post by piratesmack on 2008-03-30
> **prshah said:**
> Simple version: 
one "/" partition, 10~15gb in size
1 swap partition 1Gb~2Gb in size
everything else "/home"

Complex version: (Not recommended)

Ideal partitioning tips:
/- Root file system. Should just contain /bin, /sbin, /dev, /root,       /lib and /etc.
Min: 100Mb	Max: 100Mb
---	---	---
/usr- Programmes and source code. 
Min: 300Mb	Max: 2Gb+
---	---	---
/var-Variable data, such as spools, man pages, news and mail        queues, database data.
Min: 400Mb	Max: 400Mb+
---	---	---
/boot-Boot kernels
Min: 20Mb	Max: 20Mb
(recommended 1st primary partition)
---	---	---
/home-User data and "stuff".
Size depends on estimated size of user data.
Min: 50Mb(?)	Max:Anything
---	---	---
/tmp-Temporary file locations
Size depends on usage. Eg. scanning of large files, etc.
---	---	---
Recommended additional partitions:
/usr/local- Ideal place to install 3rd party software
---	---	---
/var/spool/squid- recommended if proxy server
---	---	---
/var/log- recommended since log if partitioning fills up, only logging will be stopped, with no effect to rest of the system.
--	--	--
Recommended to have swap partition in the "physical" centre of the HDD.

Hope this helps and doesn't confuse.


Thanks

Also, is it possible for 2 linux distros to share a /home partition?

---

### Post by Oldsoldier2003 on 2008-03-30
> **rajaram_s said:**
> isnt a /boot parition useful for recovering grub if its lost? I had the same kind of problem. I tried installin fedora on my comp which had ubuntu and vista in it. Is it possible to recovermy ubuntu? The fedora boot loader just shows fedora and vista in it... I gave a seperate /boot partition durin the installation of ubuntu but not during the installation of fedora.

Yes you can recover. fedora just installed grub again in its partition. you should be able to edit menu.lst to fix it. [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817) is a tutorial on Multi-booting

---

### Post by Oldsoldier2003 on 2008-03-30
> **piratesmack said:**
> Thanks

Also, is it possible for 2 linux distros to share a /home partition?

Yes, just be careful, two widely disparate distributions could cause your configuration files to go a little bit nuts.

---

### Post by piratesmack on 2008-03-30
> **Oldsoldier2003 said:**
> Yes, just be careful, two widely disparate distributions could cause your configuration files to go a little bit nuts.

Thanks

---

### Post by rajaram_s on 2008-03-30
menu.lst of fedora or ubuntu (using a live cd)?

---

### Post by prshah on 2008-03-30
> **piratesmack said:**
> 
Also, is it possible for 2 linux distros to share a /home partition?

Short answer: Yes

Long Answer:
[http://ubuntuforums.org/showthread.php?t=725314&highlight=prshah+shared+home](http://ubuntuforums.org/showthread.php?t=725314&highlight=prshah+shared+home)

Please READ WARNING IN LONG ANSWER before proceeding.

---

