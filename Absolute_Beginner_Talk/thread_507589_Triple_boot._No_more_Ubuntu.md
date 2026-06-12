---
title: "Triple boot. No more Ubuntu"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Maxwelinux on 2007-07-23
Hi

I got XP and Ubuntu 7.04 and try to install CentOS.

During the installation of CentOS, I choose

-to install a new bootloader and it scratch my old grub in the /MBR with it's own data
-use the same swap as Ubuntu bu re-format it.

So now I can boot on windows and CentOS but not Ubuntu anymore.
As I tried to configure my CentOS and as I do not like it, I really look forward my Ubuntu feisty available again.

So I suppose that I can do something like the following :

1 - Use my Win 98 bootable CD, boot on it and make a 

[FONT="Courier New"]**fdisk /MBR**[/FONT]

2 - use a Ubuntu CD to boot on it. I just get the Dapper one. Do i need the 7.04 one?
3- reinstall just the grub.
4- tell the grub to use the grub.conf that should be still present on the / partition of my Ubuntu 
5- reboot and log on my ubuntu partition
6- tell the system to use the swap space that I have previously use for CentOS

Could you
- tell me if this scenario is OK
- answer question on point 2
- if this is OK, I would like to know the way to achieve point 3,4 and 6

Thanks in advance and Ubuntu for ever. :guitar:

Max

---

### Post by logos34 on 2007-07-23
> 2 - use a Ubuntu CD to boot on it. I just get the Dapper one. Do i need the 7.04 one?
3- reinstall just the grub.
4- tell the grub to use the grub.conf that should be still present on the / partition of my Ubuntu
5- reboot and log on my ubuntu partition
6- tell the system to use the swap space that I have previously use for CentOS

Go with that.  You can use any livecd.  Restore Grub to mbr and then add CentOS entry to /boot/grub/menu.lst.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=catlett+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=catlett+grub)

---

### Post by Wim Sturkenboom on 2007-07-23
If centos uses grub as well, the following alternative is also possible:

boot centos
mount ubuntu partition containing ubuntu's /boot
find ubuntu's menu.lst
edit ubuntu's menu.lst as well as centos' menu.lst and copy the relevant entry for ubuntu to centos' menu.lst

---

### Post by Maxwelinux on 2007-07-24
> **logos34 said:**
> Go with that.  You can use any livecd.  Restore Grub to mbr and then add CentOS entry to /boot/grub/menu.lst.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=catlett+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=catlett+grub)

Hi..Thanks it works..with a Dapper CD..

Pfiou..my next triple boot will be with Debian Etch...No Red Hat Family..[-([-X

---

