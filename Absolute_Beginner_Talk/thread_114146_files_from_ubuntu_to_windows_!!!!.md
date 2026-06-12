---
title: "files from ubuntu to windows ?!?!?!?!"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by djlilyazi on 2006-01-07
Hi,

if i have a file i want from ubuntu and i want to get it from windows is that possible ? win and ubuntu is sepret partitions....

thanks

YAZ

---

### Post by aysiu on 2006-01-07
You need a separate FAT32 partition or FAT USB drive or pen drive... or email it to yourself...

---

### Post by ptmurphy on 2006-01-07
[QUOTE=djlilyazi]Hi,

if i have a file i want from ubuntu and i want to get it from windows is that possible ? win and ubuntu is sepret partitions....

thanks

YAZ[/QUOTE]

Sure, if the file is in the same physical system, just mount the windows drive.  In the start guide under help there is a good section on mounting windows drives.

If the file is on another system on the network, you will probably want to install Samba to allow network file and folder sharing between the two systems.

---

### Post by aysiu on 2006-01-07
[QUOTE=ptmurphy]Sure, if the file is in the same physical system, just mount the windows drive.  In the start guide under help there is a good section on mounting windows drives.[/quote] Writing to NTFS from Ubuntu is not a good idea.

---

### Post by djlilyazi on 2006-01-07
[QUOTE=ptmurphy]Sure, if the file is in the same physical system, just mount the windows drive.  In the start guide under help there is a good section on mounting windows drives.

If the file is on another system on the network, you will probably want to install Samba to allow network file and folder sharing between the two systems.[/QUOTE]

what i mean is...like...i have files on my ubuntu but i am using windows ..so how can i access ubuntu from win xp ?

---

### Post by Qrk on 2006-01-08
[http://www.fs-driver.org/](http://www.fs-driver.org/)

I have never used it myself; so I can't endorse it.

But no one had a problem with it on the forums, so it can't be that bad.

---

### Post by robie69 on 2006-01-08
I use Ext2Fsd. it's an open source DOS program. 
download it here.
[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

---

