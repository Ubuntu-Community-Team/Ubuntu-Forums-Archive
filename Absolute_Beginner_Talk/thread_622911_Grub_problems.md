---
title: "Grub problems"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by William S on 2007-11-25
I had to install Ubuntu on my PC after it had become slower, alright all well until it installs GRUB. I get error 15. And super GRUB didnt work, although it works to load Windows...

---

### Post by Pumalite on 2007-11-25
Post your complete specs. And what iso did you use?.

---

### Post by William S on 2007-11-25
My specs are
AMD 64 3000+ 
2048 MB RAM 
2X 250 GB HDD 
ATI x550 video card 

And I am using the free CD 32 bit sent from Ubuntu. 
Previously I had the 64 bit edition, maybe this can have something to do with it?

---

### Post by linux noooob on 2007-11-25
this guy had the same problem with gentoo look at it [http://www.linuxquestions.org/questions/fedora-35/grub-error-15-431469/]("http://www.linuxquestions.org/questions/fedora-35/grub-error-15-431469/")

---

### Post by William S on 2007-11-25
But the problem seems to lie on GRUB and not Ubuntu itself.

---

### Post by linux noooob on 2007-11-25
well it could be like the forum post said that something was not named right or grub is not picking up the Ubuntu partition or overall the partition is not flagged as boot able.

---

### Post by alienexplorers on 2007-11-25
Try doing a:
> sudo fdisk -l
and post the output here.

---

### Post by Pumalite on 2007-11-25
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by William S on 2007-11-25
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1045     8393931   83  Linux
/dev/sda2            1046       30400   235794037+   7  HPFS/NTFS
/dev/sda3           30401       30401        8032+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2aff8c51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19574   157228123+   7  HPFS/NTFS
/dev/sdb2   *       22125       29126    56243565   83  Linux
/dev/sdb3           29127       30160     8305605    7  HPFS/NTFS
/dev/sdb4           19575       22124    20482875   83  Linux



My output of your command. Ran from Live Cd...

---

### Post by Pumalite on 2007-11-25
Windows is in sda2 and Ubuntu in sda1. Did you install Windows after Ubuntu?

---

### Post by William S on 2007-11-25
No I did not... 
Maybe that is the Master Boot Sector.

---

### Post by Pumalite on 2007-11-25
You have boot flags in sda1 and sdb2. Which one are you trying to boot?.

---

### Post by William S on 2007-11-25
Well, the boot flag in sdb 2 is there by a mistake. 
sda 1 is the right one as that is the Windows partition. 
Maybe everything went wrong as I now defined seperate / and ./home partitions?
As I only had partition with the whole thing before...

---

### Post by Pumalite on 2007-11-25
No. sda1 is another Linux partition.

---

### Post by William S on 2007-11-25
Well I found out a thing. I booted up a Gparted live CD. It says SDA is a FAT32 partition, and I think it is my Windows recovery partition.

---

### Post by Pumalite on 2007-11-25
Funny that your
sudo fdisk -lu
would show it as a Linux partition.

---

### Post by William S on 2007-11-25
Yeah, but Gparted says it's FAT. Well when I had the boot flag on SDA 1 it jumped right into the Recovery Console of my Windows. I think something went wrong when formatting to EXT 3, and I think I'll attempt a reinstall just to see how it works, with just one root partition and without the /home one...

---

### Post by Pumalite on 2007-11-25
Good idea. I'll tell you; those recovery partitions are a lot of problems. You cannot let Grub install itself there. In your case, it has to be sda2 if I remember well. In step 7, in 'Advanced Tab', you can change where Grub installs.

---

### Post by William S on 2007-11-26
But still it was strange it worked before...
And if I install GRUB in the first sector of the Ubuntu partition how would I load it then?

---

