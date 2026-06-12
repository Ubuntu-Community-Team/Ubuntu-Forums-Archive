---
title: "[Help]Grub Error 17"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by c_coolguy on 2006-11-24
hi, i recently installed vista](*,)  on my pc and tried to fix gub using live cd. but after rebooting my pc it says:
Error 17 : Cannot mount selected partition
do anyone has a hint on how to fix the problem? Thanks~~

grub> root (hd0,2) 
Filesystem type is ext2fs, partition type 0x83 

grub> setup (hd0) 
Checking if "/boot/grub/stage1" exists... yes 
Checking if "/boot/grub/stage2" exists... yes 
Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 15 sectors are embedded. 
succeeded 
Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2 
/boot/grub/menu.lst"... succeeded 
Done.

---

### Post by c_coolguy on 2006-11-24
PS. i can boot vista normally using grub....
Thanks again

---

### Post by adam.tropics on 2006-11-24
Just to clarify, you can boot vista via grub, just not Ubuntu?

---

### Post by c_coolguy on 2006-11-24
yeah, i'd rather vista couldnt be loaded....

---

### Post by Psquared on 2006-11-24
How did you fix it? I have the same problem.

I noticed in fstab that the windows partition is commented out. Could that have anything to do with not being able to mount the partition in GRUB?

---

### Post by adam.tropics on 2006-11-24
try reinstalling grub again. and if you didn't already, [use this guide.]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd")

---

### Post by Psquared on 2006-11-24
> **adam.tropics said:**
> try reinstalling grub again. and if you didn't already, [use this guide.]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd")

Thanks - I'll give it a try.

In my case upgrading to Edgy is what borked the Windows Chainloader. It wasn't even listed in grub/menu.lst. I tried to manually edit /boot/grub/menu.lst by adding the typical Windows entry but that is where it choked. I've tried mapping and then I tried Super Grub all to no avail. About as far as I get is "unable to mount partition." Windows (Vista RC1) is on hda2 according to fdisk -l. So my question is will restoring GRUB this way find the Windows partition and insert the correct command? Ubuntu boots fine.

---

### Post by Psquared on 2006-11-24
Oh - one more thing. The live CD I have is 6.06, but I am running Edgy. Will the 6.06 live CD work anyway?

---

### Post by adam.tropics on 2006-11-24
It should do.....! I was gonna say, if worst comes to worse, now vista etc is already installed a fresh install would solve it, but since you have dapper cd keep that for last resort only!

oops...read wrong post...should do applies to both!

---

### Post by Psquared on 2006-11-24
Thanks - will give it a try this afternoon.

---

### Post by kenweill on 2006-11-24
Try [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Psquared on 2006-11-24
I've tried the Wiki suggestions. Heck I've tried Super Grub too and it can't find the Windows partition and boot it. It's there because fdisk -l says it is, but it won't boot ever since I upgraded to Edgy from Dapper.

---

