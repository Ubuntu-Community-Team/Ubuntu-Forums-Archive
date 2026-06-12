---
title: "Accidentally overwritten FAT, need to recover partitions!"
date: 2012-10-06
forum: Any Other OS
---

### Post by tozhan on 2012-10-06
Hi guys, I just gave myself a massive heart attack!

So I was rejigging the boot sector of a USB device when I identically wiped the wrong drive using fdisk. 

My 320Gb drive is now screwed, it should still contain my windows 7 install, Ubuntu 12.04 install, swap disk and maybe one for grub but Im not too sure how that works.

Which tool is best to recover the partitions?? The data is valuable so I cant just reinstall. Also I cant boot into either so I need a bootCD solution if possible. Hope you can help!

Thanks

Tom

---

### Post by tozhan on 2012-10-07
OK, I have managed to recover the linux partition and the swap. According to testdisk the windows partition is unrecoverable due to the MFT and backup MFT being 'bad'. So anyone know any cool tricks or is it time to break out the file recovery software and do the old OS rebuild??

---

### Post by mips on 2012-10-07
Do you have any data on the win partition. Should be able to easily recover the data but not so sure about restoring the OS short of inserting the original disk and trying to run a repair or else a fresh install.

---

### Post by tozhan on 2012-10-07
Yeah ill have to pull that data off sometime tomorrow. I tried to use the windows disc but it didnt even recognise the OS to repair it and just offered a new install. Guess I know what im doing monday morning...

---

