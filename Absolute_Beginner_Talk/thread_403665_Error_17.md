---
title: "Error 17"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by metzy85 on 2007-04-07
i get some error 17 when i turn my computer i have scearched through the forums and all of them say u need to boot form ur xp cd but i have a dell and it does not have xp cd i do not have one so is there away to fix mbr without cd

---

### Post by Hieronymus on 2007-04-07
Download [fixmbr]("http://www.ambience.sk/experiments/MbrFix.exe") 
[LIST=1]
[*]Create any bootable floppy disk/diskette A: (even with older Windows systems)
[*]Run MbrFix to see the current list of partitions: mbrfix /drive 0 listpartitions
[*]Run MbrFix in the following way: mbrfix /drive 0 fixmbr
[*]If you have more than 1 physicial hard disk (hard drive), you have to use proper number for your disk. E.g. change 0 to sdifferent number (1, 2 etc.)[/LIST]you can download a bootable floppydisk [here]("http://www.bootdisk.com/")

I found this info [here]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php")

---

### Post by Maestro23 on 2007-04-07
> **Hieronymus said:**
> Download [fixmbr]("http://www.ambience.sk/experiments/MbrFix.exe") 
[LIST=1]
[*]Create any bootable floppy disk/diskette A: (even with older Windows systems)
[*]Run MbrFix to see the current list of partitions: mbrfix /drive 0 listpartitions
[*]Run MbrFix in the following way: mbrfix /drive 0 fixmbr
[*]If you have more than 1 physicial hard disk (hard drive), you have to use proper number for your disk. E.g. change 0 to sdifferent number (1, 2 etc.)[/LIST]you can download a bootable floppydisk [here]("http://www.bootdisk.com/")

I found this info [here]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php")

Beat me to it. Found the exact same link when I was googling.  :)

---

### Post by Hieronymus on 2007-04-07
> **Maestro23 said:**
> Beat me to it. Found the exact same link when I was googling.  :)

:lolflag:

---

### Post by metzy85 on 2007-04-07
thank you very much i have also had dell send me a xp cd so i have one cause this is a big hassel not having one

---

### Post by Maestro23 on 2007-04-07
> **metzy85 said:**
> thank you very much i have also had dell send me a xp cd so i have one cause this is a big hassel not having one

THAT was going to be my next suggestion to you.:)

Good luck man.

---

### Post by n3gbz on 2007-04-07
Additionally, you may want to look at your /boot/grub/menu.lst file using a live CD (I usually use Knoppix) 

Grub error 17 is:  

17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Typically when I have had this error, I simply needed to change my GRUB root commands from 
 
root (hd0,3)    --   to     --   root (hd0,4)

(I have multiple partitions and Ubuntu often gets my boot partition number off by 1 and tries to boot from the wrong partition)

---

