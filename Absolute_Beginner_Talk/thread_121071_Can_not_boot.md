---
title: "Can not boot"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by lengguard on 2006-01-24
I have tried to boot the live and install cd with no success.Is my cd rom the problem.celeron 667 128 ram.

---

### Post by rjwood on 2006-01-24
Is your system reading your cd rom drive at start-up? If not go into your BIOS and tell it to. 

As your system is starting- you are given an option to go to the BIOS set up by pressing an (F) key.

---

### Post by Mustard on 2006-01-24
[QUOTE=rjwood]Is your system reading your cd rom drive at start-up? If not go into your BIOS and tell it to. 

As your system is starting- you are given an option to go to the BIOS set up by pressing an (F) key.[/QUOTE]


.. or even the DEL key on some systems will allow entry into the BIOS.

Lengguard, you would need to change the boot priority so that the CD boots before the hard drives do.

---

### Post by th2 on 2006-01-24
[http://revereradionetwork.com/phpBB2/viewtopic.php?t=3370](http://revereradionetwork.com/phpBB2/viewtopic.php?t=3370)

This guy tried to boot from a Live CD and failed.  They even changed the BIOS settings to boot off the CD-ROM drive, and it **still** failed.  Any ideas as to what the problem might be?

---

### Post by rjwood on 2006-01-24
[quote=th2][http://revereradionetwork.com/phpBB2/viewtopic.php?t=3370]("http://revereradionetwork.com/phpBB2/viewtopic.php?t=3370")

This guy tried to boot from a Live CD and failed.  They even changed the BIOS settings to boot off the CD-ROM drive, and it **still** failed.  Any ideas as to what the problem might be?[/quote]

He may have burned it too fast----I do it at 4x.

---

### Post by dueY on 2006-01-24
You have to burn the CD as an image, as well.

---

### Post by george_apan on 2006-01-24
[QUOTE=th2][http://revereradionetwork.com/phpBB2/viewtopic.php?t=3370](http://revereradionetwork.com/phpBB2/viewtopic.php?t=3370)

This guy tried to boot from a Live CD and failed.  They even changed the BIOS settings to boot off the CD-ROM drive, and it **still** failed.  Any ideas as to what the problem might be?[/QUOTE]
If he has a floppy drive he could try booting with smart boot manager:
[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

I changed my laptop's dead DVD with a CD-Rom drive and since then it refuses to boot from it even if I set everything right in the BIOS. SBM did the trick.

---

### Post by Trajik on 2006-01-24
[QUOTE=george_apan]If he has a floppy drive he could try booting with smart boot manager:
[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

I changed my laptop's dead DVD with a CD-Rom drive and since then it refuses to boot from it even if I set everything right in the BIOS. SBM did the trick.[/QUOTE]

im that guy, thanks ill try this

---

### Post by lengguard on 2006-01-24
Ihave set the bios and put a new dvd burning rom in and still cant boot .is there a iso image I can download to boot

---

### Post by george_apan on 2006-01-25
[QUOTE=lengguard]Ihave set the bios and put a new dvd burning rom in and still cant boot .is there a iso image I can download to boot[/QUOTE]
Have you tried Smart Boot Manager? I give the link a couple of posts above. You need to have a floppy drive though.

And I'm not sure you're burning the disks correctly. You should burn the .iso image directly, not as a file in a data disk. Do it with right-clicking on the .iso file and select burn image.

---

### Post by cotcot on 2006-01-25
Can you boot from other bootable CD's ? For instance the installation CD of your OS or a Knoppix CD or so ? If no it has to do something with your hardware or BIOS setting. I had once the case that i could not boot from floppy because the floppy drive was not enabled although it was the first in line to boot from. 

Do you have 2 CD drives ? If yes, try the other one. (may sound stupid, but sometimes stupid things are overlooked)

---

### Post by rjwood on 2006-01-25
[quote=lengguard]Ihave set the bios and put a new dvd burning rom in and still cant boot .is there a iso image I can download to boot[/quote]

go to the wiki and search 'iso', you wil find breezy page for downloading.  Good Luck!!

---

