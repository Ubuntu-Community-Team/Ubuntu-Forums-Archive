---
title: "Partitioning a hard drive before install"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by k0ontz on 2005-11-06
Hi, 

I'm going to be installing Ubuntu within a few days, but first I *need* to partition a hard drive that uses the NTFS file system with Windows XP installed on the one, current partition. Ill be spliting this drive into about 3 10gb sections, with the reaminder left for windows. I have the Ubuntu live CD, but im not to sure whever GParted would work with NTFS. It has to be done through any boot CD, and not with Windows. Any sugestions on how to do this are relly appreciated.

---

### Post by gord on 2005-11-06
the partitioner you get with the ubuntu installer can resize windows xp partitions just fine :) least it did fine with me. i think gparted would do fine too. but, as allways with large opperations, allways pays to backup first.

---

### Post by k0ontz on 2005-11-06
Yeah, the actuall computer gets reimaged every month or so, and all data is stored on a network drive. The only "real" data on the computer is the Windows install, and a few apps. So, im not to worried about data lost, and will Ubuntu run fine on a HD using NTFS?

Thanks

---

### Post by gord on 2005-11-06
ubuntulinux uses its own partition and filesystem (ext3) which is created during the install, you will have to resize your other partitions at that point to make space for ubuntu. you will still be able to access your files on your ntfs partitions but its generally not a good idea to write to an ntfs partition from linux. reading from one is just fine though.

---

### Post by k0ontz on 2005-11-06
But i need to resize partions *before* i install Ubuntu. Will the easiest thing be to use GParted on the Live CD, then when I come back in a few days, install Ubuntu onto one of the new Partitions?

After all is said and done, the HD will look like this?

-10gb with Ubuntu on it (ext3)
-10gb Empty
-10gb Empty
-Remainder Windows (NTFS)

---

### Post by gord on 2005-11-06
im sure you could partition it with the live cd using gparted just fine :) allthough having two partitions that are empty is rather silly, you could leave 20gb as unpartitioned space or have them as fat32 partitions for sharing data between opperating systems. but its upto you :)

---

### Post by k0ontz on 2005-11-07
Yeah, but 2 other Linux disrtos will be installed allong side Ubuntu and WinXP. A quad boot system I guess. One last question, how do you install a boot loader? Will I install it when I install Ubuntu, or When I partition the Hard Drive. 

Thanks.

---

### Post by Darrin on 2005-11-07
[QUOTE=k0ontz] how do you install a boot loader? Will I install it when I install Ubuntu, or When I partition the Hard Drive. 

Thanks.[/QUOTE]
Grub (the bootloader) will prompt you if you want to install it during the installation of ubuntu.

---

