---
title: "help! grub issue"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by madu nag on 2007-07-31
i dual booted ubuntu 6.06 (dapper) & win XP on my computer

intel pentium D 2.80 Ghz (processor)
ASUS P5PE-VM (mobo)
NVidia GeForce4 MX 440 agp 8x (VGA)
512 ram

but the device manager shows 'Device: Unknown' for the processor.
and the system monitor shows only one CPU graph.
and althow i installed the nvidia drivers for the vga with 'easy ubuntu' i am not sure if that worked (i get blue backgrounds when i move a media player window as it plays video).

so i tried the feisty 7.04 live cd and it tried to download nvidia drivers and showed the two processors.

but when i tired to install feisty it went ok till at the end,
it gave an fatal error while installing the GRUB.
when i restarted there was a grub error and i had to reinstall 6.06.

is there any way to remove the grub from the master HDD?
(i have ubuntu in the slave and XP in the master)
will there be a problem if i have to reinstall XP?

---

### Post by MQMike on 2007-07-31
You can run the Windows CD and it has a recovery option on it somewhere, with which you can restore the Master Boot Record of your Windows drive (ie, no need to re-install all of Windows).
That will overwrite anything that GRUB put in the MBR of that drive, so then how will you boot into Ubuntu?
The whole story is told in the following:

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

(Look at the stuff about re-installing GRUB.  If GRUB is installed correctly to the MBR of your first bootable hard drive (which I think is your Windows drive, right?), it will then boot both Windows and Ubuntu for you.)

---

### Post by madu nag on 2007-08-07
Sorry it took so long to reply.
I will read the links.
But is there any way to update dapper to feisty using the feisty cd? (possibly with no internet). 
Thanks for all your help,

madhawa

---

