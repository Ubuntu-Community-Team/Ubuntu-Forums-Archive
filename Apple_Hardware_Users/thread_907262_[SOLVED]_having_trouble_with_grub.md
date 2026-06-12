---
title: "[SOLVED] having trouble with grub"
date: 2008-09-01
forum: Apple Hardware Users
---

### Post by kylegio on 2008-09-01
hey, so i finally got my tri-boot to work, but i think i may have installed grub incorrectly... i am using refit so the refit menu comes up, however both the linux and windows options take me to grub, from grub i can then select windows or kubuntu, what i wanted to do is have the windows in refit boot windows using the windows bootloader, and the linux use grub, keeping them seperate, so if i tell it to boot windows i dont have to tell it to boot windows again when grub comes up....

can anyone help me fix that up, i really dont want to have to install everything again, im not familiar with grub really at all so i could use a helping hand


thanks
kyle

---

### Post by Bucky Ball on 2008-09-01
You could try using supergrubdisk but that will put everything in a grub menu. Download, make a cd and boot from that.

[www.supergrubdisk.org](www.supergrubdisk.org)

Have a bit of a read and look about - you can learn a lot from this excellent site regarding grub. In fact, with some astute research there, you could probably tweak your grub manually to do exactly as you want. 

Good luck with it ... :)

---

### Post by kylegio on 2008-09-01
i just assumed there must be a way for me to get into windows without grub, i mean using rEFIt there are options to boot windows and options to boot linux, but if they both take me to grub whats the point? there has got to be a way so that when i tell it to boot windows it doesn't look at grub at all...all im saying is i dont want grub to be the boot loader for my windows OS, however i want to keep it for my linux installation


if i cant do that, then how can i change grubs config's , ill just make windows the default OS in grub (if thats possible) . i just hate having to go through a series of menu's to get into windows

---

### Post by cyberdork33 on 2008-09-01
You install GRUB to the Ubuntu partition and then install the windows bootloader into the MBR. Then refit will start each directly. 

First install GRUB to the Ubuntu partition like is shown here:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

Then use the Windows CD and the Recovery console to 'FIXMBR' will will reinstall the Windows bootloader to the MBR.

---

### Post by kylegio on 2008-09-01
> **cyberdork33 said:**
> You install GRUB to the Ubuntu partition and then install the windows bootloader into the MBR. Then refit will start each directly. 

First install GRUB to the Ubuntu partition like is shown here:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

Then use the Windows CD and the Recovery console to 'FIXMBR' will will reinstall the Windows bootloader to the MBR.

no dice, cant get into the recovery console... first i cant load bootdisks, they never work on my computer, no live cds work ever

i got it to work by installing the recovery console to the windows boot options, it starts up the recovery console and the loading bar finishes then just blue screen of deaths "UNMOUNTABLE_BOOT_VOLUME"

any other way to fix the mbr?

---

### Post by kylegio on 2008-09-01
used mbrfix from windows, worked like a charm, you're a legend man thanks

---

### Post by cyberdork33 on 2008-09-01
please mark this thread as solved (thread tools menu)

---

