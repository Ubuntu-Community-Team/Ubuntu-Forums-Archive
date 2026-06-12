---
title: "where can I find info on how to ERASE UBUNTU and GRUB"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by donamai on 2007-04-20
Hi,

I have been trying to learn Ubuntu but I see is more complicated than I expected. 

Anyone know how to remove the GRUB and UBUNTU from my system?

Thank you!

---

### Post by arsadogi on 2007-04-20
have other opperating systems except ubuntu in the same disk ?.for example dual boot with an xp.

---

### Post by Sef on 2007-04-20
> have been trying to learn Ubuntu but I see is more complicated than I expected.


What have you found complicated?

---

### Post by lotacus on 2007-04-20
it all depends on what other operating system you are going to install. Well, not really, but  you could use the live cd, booting from it and delete the partition. I am not sure about what can be done in the console regarding the boot sector, however, this isn't an issue since another OS install will overwrite the boot sector.

Another method would be during the installation of windows. You have the option to select which partition you want to install to. It will list the partitions and unknown partitions. You can select the unknown partition and press D for delete. Easy as that.

---

### Post by tonygod on 2007-04-20
The answer to your question is to put in the CD or DVD for Windows or OSX or whatever it is you want to move back to and re-partition/format the drives and re-install the OS.

If you have your old OS there somewhere still, you can get rid of GRUB by
1. Windows XP: fixmbr and fixboot by booting off the XP installation disc and going into the Recovery console
2. Windows Vista: "bootrec /FixMbr" and "bootrec /FixBoot" by booting off the Vista installation disc and going to "Repair your computer->System Recover Options->Command Prompt"

---

### Post by kernow-kisser on 2007-08-16
Further to this thread, I am in a similar position:
I loaded Ubuntu onto my laptop, but erased everything on the 'C' drive. Now all I have is Ubuntu.
Whilst I'm trying to get accustomed to Ubuntu (but I'm still trying) my wife wants to run XP and Ubutnu on the laptop.
I've had to purchase a Win XP recovery disc but I cannot load it as the laptop refuses to boot from the CD and tells me that I "do not have a decoder installed to handle this file" when I double click on .dat, .exe files, etcetera.  Please help me to run Ubuntu and XP.

---

