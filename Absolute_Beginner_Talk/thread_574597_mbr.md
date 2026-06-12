---
title: "mbr"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by sandysandy on 2007-10-13
hi guys
i must be the 100 th guy who's messed up his mbr. but with this forum i am sure some one will help me out.

specs of my machine Pentium D 3 ghz. 1 GB Ram, 2 HDD
first hdd 40gb - ubuntu 7.04
second hdd 160 gb - win xp (installed first) & Ubuntu 7.04

i can boot from live CD, but cannot boot from hard disk as the following message comes
[COLOR="Red"]Isolinux: Disk error 01, AX=0201, drive 80[/COLOR]

thanx

---

### Post by alienexplorers on 2007-10-13
Does the boot error occure before or after the grub loader or what ever loader you are using.

---

### Post by sandysandy on 2007-10-13
thanx for ur prompt reply

when i boot from HDD the grub loader comes up with variou options for booting like

 linux kernel...
Win XP etc

when i select any choice, " error booting.." comes up.
when booting from live Cd, when i choose " boot from first hard disk"
error message "Isolinux: Disk error 01, AX=0201, drive 80" comes.

i can however boot from the live CD with no problem. Booting from HDD is not happening.

thanx again:guitar:

---

### Post by louieb on 2007-10-13
If you are getting the GRUB menu that means the code in the MBR is working correctly. It only about 400-500 bytes long and its only job is to pass execution to your boot loader program (stage2 in the case of GRUB). 

Really sounds like the hard drive itself has major problems. 

If you have internet with the live CD I want you to post the partition table
Applications>accessories>terminal> ```
sudo fdisk -l
``` (lowercase L) and post the output

After looking at the partition table, may need the content of /boot/grub/menu.lst.  

You can use applications>accessories>text editor to copy its contents,

---

### Post by sandysandy on 2007-10-13
thanx 

[COLOR="Red"]the output of sudo fdisk -l is as follows:-[/COLOR]

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         280     2249068+  83  Linux
/dev/sda2            4559        4865     2465977+  82  Linux swap / Solaris
/dev/sda3   *        2362        4558    17647402+  83  Linux
/dev/sda4             281        2361    16715632+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188       16581   107587305    f  W95 Ext'd (LBA)
/dev/sdb3   *       16582       19457    23101470   83  Linux
/dev/sdb5            3188        8286    40957686    7  HPFS/NTFS
/dev/sdb6            8287       13385    40957686    7  HPFS/NTFS
/dev/sdb7           13386       16451    24627613+   7  HPFS/NTFS
/dev/sdb8           16452       16581     1044193+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by az on 2007-10-13
> **sandysandy said:**
> 
i can boot from live CD, but cannot boot from hard disk as the following message comes
[COLOR="Red"]Isolinux: Disk error 01, AX=0201, drive 80[/COLOR]

thanx

Actually, I think this is a bug in your BIOS.

I take it everything else was working fine before you installed Ubuntu?

There is no way for GRUB to boot since it is not able to talk to your hardware and tell it how to boot.  Perhaps you can try booting the live cd, chrooting into your Ubuntu install and installing LILO instead of grub?  Or maybe another bootloader?

[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by sandysandy on 2007-10-13
thats right win xp was working fine before i installed ubuntu.

should i change to lilo or give GRUB one more try.

regards

---

### Post by louieb on 2007-10-13
I haven't had your problem but I am inclined to agree with az.  The fdisk output look fine. 

I take it you have Ubuntu on your 40 gig drive and XP on the 160 gig drive. Did you install the 40 gig drive just before installing Ubuntu?  What type of drives are they. (ide sata..)? There have been some problems configuring the boot loader when mixing ide and sata drives on the same computer. 

Haven't used LILO so don't know if it would have the same problem. Might try it. Or try GAG. If worse  come to worse you can always  change the MBR back to booting windows.  Then see if theres a BIOS update for your PC. 

I use the site az pointed to quite a bit.  It has sections on LILO, GAG, and restoring the MBR to boot Windows. 

[IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
[IDBS GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")
[IDBS WinGrub (NTLDR) and Ubuntu]("http://users.bigpond.net.au/hermanzone/p9.html")
 
Good luck.

---

### Post by sandysandy on 2007-10-14
the 40GB HDD is IDE and the 160GB HDD is SATA.

ur right in saying that the 40GB hdd may be having problem. this may be because it is an older disc (IDE about 4 years old from my previous computer) and may not be compatible with my new computer BIOS. this i could make out as i was unable to boot even windows after loading it on th older 40 GB HDD. 
however i could repair the windows MBR on the 160GB hdd and have not lost any data.
i will try loading ubuntu on one partition of the newer 160GB hdd as the older 40 Gb hdd is not seeming to be bootable with Intel Pentium D 2 core machine with either windows or linux, though the hdd is ok as far as storing data is concerned.

regards

---

### Post by sandysandy on 2007-10-31
after going through the forums, i am getting a good idea on installing Ubuntu.
i am now planning to reinstall ubuntu on the 160 SATA hdd as previous attempts on 40gb IDE hdd have been unsuccessful.
(system specs Pentium D (64bit) 3.00GHz, 1GB RAM, 160GB SATA hdd (Win XP) and 40GB IDE hdd (Gutsy 7.10)
would appreciate help on following:-

1.  how to backup MBR on 160 GB SATA hdd which is running Windows XP,  prior to loading Gutsy on it, so that i can restore MBR, if it gets corrupted.
2.    How to restore MBR, if it gets corrupted.
3.   Any other suggestion prior to loading Gutsy on Hdd already having Win XP on another partition.

thanx

---

### Post by sandysandy on 2007-11-01
how do i backup my windows MBR before installing Gutsy on it.
:confused:

---

### Post by rbc on 2007-11-01
check dcstar's post here:
[http://ubuntuforums.org/showthread.php?t=56723&highlight=bs%3D446&page=4](http://ubuntuforums.org/showthread.php?t=56723&highlight=bs%3D446&page=4)

---

### Post by sandysandy on 2007-11-03
> **rbc said:**
> check dcstar's post here:
[http://ubuntuforums.org/showthread.php?t=56723&highlight=bs%3D446&page=4](http://ubuntuforums.org/showthread.php?t=56723&highlight=bs%3D446&page=4)

thanks.

that was a good link. 

regards

---

