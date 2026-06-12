---
title: "my brother deleted his ubuntu partition, problem booting up."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by rodami on 2007-07-03
Hello, my brother had a dual boot with vista and ubuntu, and he deleted the ubuntu partition. But know, everytime the pc starts, instead of booting up to vista, he gets an error message that says, 

   Grub loading stage 1.5 
   Grub loading, please wait...
   Error 22

and the screen just stays there instead of booting up Vista, what could be wrong? and how could I fix it, I tried doing system restore with the vista cd but nothing, and he has some important documents he wants to at least backup if formatting is necesarry.
Thanks.

---

### Post by Vajra Vrtti on 2007-07-03
What is wrong is that grub was inside the deleted partition. The easiest way to correct that is just to reinstall Ubuntu, and the installation process will identify you Vista again. Otherwise you will have to use Microsoft tools to restore the disk MBR to boot Vista directly.

---

### Post by confused57 on 2007-07-03
> **rodami said:**
> Hello, my brother had a dual boot with vista and ubuntu, and he deleted the ubuntu partition. But know, everytime the pc starts, instead of booting up to vista, he gets an error message that says, 

   Grub loading stage 1.5 
   Grub loading, please wait...
   Error 22

and the screen just stays there instead of booting up Vista, what could be wrong? and how could I fix it, I tried doing system restore with the vista cd but nothing, and he has some important documents he wants to at least backup if formatting is necesarry.
Thanks.
You could reinstall Ubuntu, which should enable booting into Vista...then you could MbrFix.exe to restore Vista's bootloader to the mbr:
[http://ubuntuforums.org/showthread.php?p=2809942#post2809942](http://ubuntuforums.org/showthread.php?p=2809942#post2809942)

---

### Post by rodami on 2007-07-03
Ok, I tried reinstalling ubuntu, but everytime I try to resize the partition, its says there is an error and can't do it.
By the way, there is only one partition now, the vista one.

---

### Post by Vajra Vrtti on 2007-07-04
Does it take all the disk?

---

### Post by rodami on 2007-07-04
vista? yeah it does, and it won't let me even partition at all, is there a way where I could just boot to vista, backup a couple of files, and format the whole thing to get it over with?

---

### Post by Vajra Vrtti on 2007-07-04
I don't know about Vista, but in Windows XP you could boot from the installation CD and use a tool named **Recovery Console**. The **fixboot** and **fixmbr** commands would restore the *boot sector* and the *master boot record *(MBR) so that the machine would boot directly into Windows again ([Microsoft document]("http://www.microsoft.com/germany/technet/prodtechnol/winxppro/reskit/z03c621675.mspx")). I've already done that and it works.

Another way would be to boot from the Ubuntu Live CD, copy the data you need to save, and to install everyting again from the beginning.

---

### Post by sailor2001 on 2007-07-04
> **Vajra Vrtti said:**
> I don't know about Vista, but in Windows XP you could boot from the installation CD and use a tool named **Recovery Console**. The **fixboot** and **fixmbr** commands would restore the *boot sector* and the *master boot record *(MBR) so that the machine would boot directly into Windows again ([Microsoft document]("http://www.microsoft.com/germany/technet/prodtechnol/winxppro/reskit/z03c621675.mspx")). I've already done that and it works.

Another way would be to boot from the Ubuntu Live CD, copy the data you need to save, and to install everyting again from the beginning.
  I keep an old MEMPIS handy to fix grub.......also you can download a copy of super grub
If you can get into your cmd on windows..fixmbr

---

