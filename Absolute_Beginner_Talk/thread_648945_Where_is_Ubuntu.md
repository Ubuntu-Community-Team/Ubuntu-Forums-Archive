---
title: "Where is Ubuntu ?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by blinded on 2007-12-24
Hi, I just want to say I am a complete noob, so please bear with me.

A few months ago this friend installed Ubuntu in my computer. I have two hard drives, one which is partitioned; so I technically have three. On one of those (it was blank) he installed Ubuntu. Supposedly when we restarted the computer it would give me the option whether to run Windows or Ubuntu. It never did. So how do I run Ubuntu, I don't have the CD by the way ?

---

### Post by chewit on 2007-12-24
You have to tell your BIOS to bring up the boot menu, I'm not sure what button you have to press before start-up. I think its F8, I may be wrong.

---

### Post by blinded on 2007-12-24
So I just go to my BIOS (I'll press all Fs :P) and look for something callled Ubuntu and enable ?

---

### Post by snypercore on 2007-12-24
did you by any chance install ubuntu THEN install another windows OS? sometimes this has happened to me and it stops the GRUB menu coming up, and VISTA just screws this process up all together, assuming you can still get into a windows based OS such as XP or VISTA, try this app to fix any boot loader issues

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

you can use a trial to fix your problem

---

### Post by Arwen on 2007-12-24
Usually F2 or Delete for BIOS..but I think the bootloader is gone..or wasn't never installed.I don't think that BIOS is involved.I might be wrong though..

---

### Post by snypercore on 2007-12-24
> **Arwen said:**
> Usually F2 or Delete for BIOS..but I think the bootloader is gone..or wasn't never installed.I don't think that BIOS is involved.I might be wrong though..

my thoughts exactly

---

### Post by blinded on 2007-12-24
Windows XP was installed before Ubuntu. I haven't reformatted or installed a new version of windows since.

---

### Post by snypercore on 2007-12-24
easyBCD could still help

---

### Post by RudolfMDLT on 2007-12-24
The earlier poster didn't mean you need to go INTO the bios and enable Ubuntu to boot - thats impossible.

On my system I press "del" to enter the bios and I press "F2" to bring up a menu which then lets me choose which hard drive to boot from.

When your PC boots, watch the bottom bit of the screen for instructions... one key to load the bios and another to bring up a boot menu. In the boot menu, then select the first drive and see what boots. restart and select the other. If Ubuntu doesn't boot on either I recommend reinstalling it yourself.

---

### Post by blinded on 2007-12-24
Alright I downloaded EasyBCD

However it only gives me the option to fix C or D. I have Ubuntu on E. If I go to my PC E has been hidden ever since I installed Ubuntu.

Let me go to the bios right now

---

### Post by snypercore on 2007-12-24
you may have to go about installing a bootloader such as GRUBB manually, i found this link that may help

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

EDIT** LOL no it wont as you cant get into ubuntu >.< have a google anyways

---

### Post by blinded on 2007-12-24
Well after fooling around I didn't get Ubuntu to work. Is there any way i can delete Ubuntu from that invincible partition so it becomes part of Windows ?

I'll delete it and try to install Ubuntu again. I am downloading Ubuntu right now.

---

### Post by zero-9376 on 2007-12-24
sounds like when ubuntu was installed it put grub (the bootloader that lets you choose which os to boot) onto the wrong hard disk, just try changing the hard disk that your computer boots from first, one of them will probably work.

---

### Post by blinded on 2007-12-24
I tried that. I have a SATA and IDE disks. I have XP installed on the SATA and Ubuntu on another partition on the SATA. I use the IDE disk just to store information. So when I tried to run Ubuntu from that specific partition in the SATA, I wouldn't find it in the BIOS.

My best bet is to install Ubuntu again. So is there any way I can reformat the parition where Ubuntu is from Windows ?

---

### Post by zero-9376 on 2007-12-24
right click on my computer go to manage and then disk/storage management, there you should be able to format the ubuntu partition/s although this isn't really necessary if you plan on reinstalling

---

