---
title: "Is GRUB neccessary?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by FarazAbbas on 2006-09-30
Im new to the whole linux thing, im an expert at windows though and i thought its time i get into linux. So i just installed ubuntu on my HD as a dualboot with windows XP. When i start my computer, GRUB starts off listing the following choices:
Ubuntu
Ubuntu Recovery
Ubuntu mem test

Windows Xp


What i want to know now is can i remove GRUB and use the windows dual boot option menu? Can i remove GRUB, put windows back into the MBR, copy the .bin file into windows and add it to the boot list, or do i have to use GRUB? Thanks, Faraz.

---

### Post by onioneater36 on 2006-09-30
I believe when you boot into windows you can do an fdisk /mbr and that will restore the windows booter into the master boot record, but I am very not sure.  I suggest that you google "fdisk /mbr" and read about that.

---

### Post by Solver on 2006-09-30
Doing fdisk /mbr from a Win98 bootdisk, or fixmbr from a WinXP setup CD recovery console will make GRUB go away. However, then it only becomes possible to boot XP.

The XP "dual boot" program won't let you boot Linux. So if you want to comfortably have the option of booting into Ubuntu or XP, you need GRUB.

The question is, why would you want the Windows menu? If there's something you don't like about GRUB, chances are, it can be fixed.

---

### Post by Herman on 2006-09-30
Possibly, you are not comfortable with Grub because it is new to you, and you have not had time to become aquainted with Grub yet.

Many people who are new to Linux and Grub would not realise that Grub is actually such a complete boot loader and manager that it is actually a small operating system in its own right. It can take commands and can be configured to do a multitude of tasks that Windows users would not even be able to imagine. 

To learn more about the Grub bootloader and what Grub can do for you, click on the following link,                       GRUB Bootloader Page.....................................................................................................[GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

There are no other bootloaders that would be comparible with Grub.

Regards, Herman :D

---

