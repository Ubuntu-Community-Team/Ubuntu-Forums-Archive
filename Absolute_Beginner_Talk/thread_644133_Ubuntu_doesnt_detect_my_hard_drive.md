---
title: "Ubuntu doesnt detect my hard drive"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Kazurik on 2007-12-18
I am completely new to Linux of any flavor and I am already stuck at installing. The Ubuntu Studio installer does not seem to detect my ATA drive while it detects my SATA drives. This is a problem as I want to put Ubuntu on the ATA as that is where I already have  Vista installed. I know that when I had previously installed Windows  XP on the ATA drive id have to push F6 during the install process so that I could specify extra drivers, and without doing that the windows install also wouldn't detect my ATA drive. I am assuming that I have to do something similar during the Ubuntu install but I don't knowhow. I do have an ASUS support CD for my mobo which has Linux drivers in its Drivers/ITE8212/Linux directory but I don't know how to use them

Any help on this would be appreciated.

---

### Post by coffeecat on 2007-12-18
Can you post the following information, please:

1 A list of all hard drives you have fitted, what types they are and to which channels they are attached. Ditto for any optical drives and any internal USB drives (such as an internal card reader). We need the latter because they are named the same way as for hard drives.

2 The motherboard chipset.

3 Boot up the live CD and open a terminal (Applications > Accessories > Terminal). Post the output of:

```
ls -l /dev/hd*
```and:

```
ls -l /dev/sd*
```This way we'll see (hopefully) exactly what the live CD is detecting and what names it is assigning. One thing you need to know is that with a fairly recent development in pata/sata kernel drivers, both PATA (ide) and SATA drives now appear as though they are SATA. (Or at least most of the time - on the machine I'm posting from atm, Ubuntu Gutsy reports my HD as hda, whereas Gentoo reports it as sda - it all depends on how and what has been compiled into the kernel). So I'm wondering if the live CD has in fact detected your PATA drive but has given it a sd* name.

Forget about the Linux drivers on the disc for now. Hopefully, the kernel will have all the drivers you need, but there are some problematic chipsets, which is why I asked for this information.


**Edit:** Forgot to mention - the output from ls -l can be quite verbose. You don't want to be typing that out. If you can get a working internet connection from the live CD, you can copy and paste from the terminal into the forum reply field.

---

