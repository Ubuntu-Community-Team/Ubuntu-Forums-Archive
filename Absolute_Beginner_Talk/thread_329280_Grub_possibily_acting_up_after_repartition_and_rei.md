---
title: "Grub possibily acting up after repartition and reinstall"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-01-01
New user here. I installed Edgy on Saturday and have been trying to get my Maudio card to work. After trying a number of suggestions that required changing setting using the terminal, I decided to reinstall to reset everything. I also decided to make a /home partition and enlarge the existing "/" partition. Bottom line I repartitioned and reformatted these partitions. The original partition where Ubuntu resided was renamed.

The install went fine but now when I boot I get the message "No OS found, please insert disk. Hit any key to continue" or something very much like that. After hitting a key I get failure messages from the computer trying to read the CD-ROM drives (third on the boot order list in the BIOS). After that Grub comes up and either OS loads fine when selected. 

I may be way off on this but I'm thinking the boot loader may have two copies of of itself in the HDD boot sector. The first looking to the old partition that no longer has Linux on it (it now has the swap partition). The second, after trying the CD-ROM drive finds the files it needs on the "\" partition.  I looked in Grub's Menu Lst and the correct (new) drives names are listed. Does this sound possible? If so how do I fix it? If not, what might it be and how do I fix it.

It's not a major problem but I'd like to fix it.

---

### Post by fasoulas on 2007-01-01
> **Patrick K said:**
> New user here. I installed Edgy on Saturday and have been trying to get my Maudio card to work. After trying a number of suggestions that required changing setting using the terminal, I decided to reinstall to reset everything. I also decided to make a /home partition and enlarge the existing "/" partition. Bottom line I repartitioned and reformatted these partitions. The original partition where Ubuntu resided was renamed.

The install went fine but now when I boot I get the message "No OS found, please insert disk. Hit any key to continue" or something very much like that. After hitting a key I get failure messages from the computer trying to read the CD-ROM drives (third on the boot order list in the BIOS). After that Grub comes up and either OS loads fine when selected. 

I may be way off on this but I'm thinking the boot loader may have two copies of of itself in the HDD boot sector. The first looking to the old partition that no longer has Linux on it (it now has the swap partition). The second, after trying the CD-ROM drive finds the files it needs on the "\" partition.  I looked in Grub's Menu Lst and the correct (new) drives names are listed. Does this sound possible? If so how do I fix it? If not, what might it be and how do I fix it.

It's not a major problem but I'd like to fix it.

By what u said u should try to fix the problem with the following link and reformat

[http://www.mainframe.gr/index.php/2006/08/28/how-to-get-rid-of-linux/](http://www.mainframe.gr/index.php/2006/08/28/how-to-get-rid-of-linux/)

---

### Post by Patrick K on 2007-01-02
I found a prog called Super Grub. I hoped it would fix the everything but I still have the problem. Looks like I'll have to re-format the drive. Thanks for the link. It lead me to a number of other options.

---

### Post by Patrick K on 2007-01-02
Boy am I red face. After setting the BIOS to boot from the CDROM first to run the Live CD, I set the BIOS to HDD1 rather than HDD0. For what ever reason the HDD0 option was several options away from the rest of the HD options. Anyway, I missed it so after spending many hours chasing my tail I can get back to configuring Edgy.

---

