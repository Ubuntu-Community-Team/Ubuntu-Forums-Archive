---
title: "How to boot ubuntu install cd? i use win2000?"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by Spyware on 2005-09-12
How to boot ubuntu install cd? i use win2000?

---

### Post by sethmahoney on 2005-09-12
You should be able to insert it in the drive and reboot, and then the install should come up.  If this isn't happening, you probably have to change some BIOS settings and enable booting from a CD.

---

### Post by Spyware on 2005-09-12
[QUOTE=sethmahoney]You should be able to insert it in the drive and reboot, and then the install should come up.  If this isn't happening, you probably have to change some BIOS settings and enable booting from a CD.[/QUOTE]


have you done it on win200?

install doesnt come

it is enabled booting from cd

i think it is something about win200

sugestions?

---

### Post by kelean on 2005-09-12
[QUOTE=Spyware]have you done it on win200?

install doesnt come

it is enabled booting from cd

i think it is something about win200

sugestions?[/QUOTE]
 First make sure that it boots off of the CD drive first.  Then with Win2000 you need to press F8 when it is booting.  If not that F2.  Been a while since I have done that on my Win 2000 pro box.  I hope that helps.

Kelean

---

### Post by GreyFox503 on 2005-09-12
Booting from a CD shouldn't have anything to do with your operating system, it has everything to do with your BIOS.  Immediately after you press the power button, and your system POSTs, you probably need to hit a key like Delete or F2 or something to enter the BIOS and change its settings.  It will tell you what key to hit during POST, but if it goes by too fast, try consulting the manual that came with your computer/mobo.

After you get into the BIOS, you need to change the order of boot devices.  Make it so that your optical drive is the first device to boot from.  Then save changes and reboot.  It should at least check the CD-ROM drive before continuing.  Of course, after you're done, you want to change the BIOS back to boot from the hard disk again.

---

### Post by Spyware on 2005-09-12
[QUOTE=GreyFox503]Booting from a CD shouldn't have anything to do with your operating system, it has everything to do with your BIOS.  Immediately after you press the power button, and your system POSTs, you probably need to hit a key like Delete or F2 or something to enter the BIOS and change its settings.  It will tell you what key to hit during POST, but if it goes by too fast, try consulting the manual that came with your computer/mobo.

After you get into the BIOS, you need to change the order of boot devices.  Make it so that your optical drive is the first device to boot from.  Then save changes and reboot.  It should at least check the CD-ROM drive before continuing.  Of course, after you're done, you want to change the BIOS back to boot from the hard disk again.[/QUOTE]


i set from bios to boot from cd rom but it still starts windoze  :neutral:  :-|  :?  :roll:

---

### Post by the_purulent on 2005-09-12
Some Motherboards (like mine) require you to press enter during the bootup process in order to boot from the cd rom.  Although it prompts me to do so...
If you have more than one drive, make sure you put it in the 'master' drive, as some will not boot from the secondary or slave drive.

-Clay

---

### Post by Spyware on 2005-09-12
[QUOTE=the_purulent]Some Motherboards (like mine) require you to press enter during the bootup process in order to boot from the cd rom.  Although it prompts me to do so...
If you have more than one drive, make sure you put it in the 'master' drive, as some will not boot from the secondary or slave drive.

-Clay[/QUOTE]


how to put it in 'master' drive?

---

### Post by GreyFox503 on 2005-09-12
[QUOTE=the_purulent]Some Motherboards (like mine) require you to press enter during the bootup process in order to boot from the cd rom.  Although it prompts me to do so...
If you have more than one drive, make sure you put it in the 'master' drive, as some will not boot from the secondary or slave drive.

-Clay[/QUOTE]

He's saying that if you have more than one optical drive, be sure to put the disc in both to test it.

Can you boot from any disc?  Even the Windows installation/recovery disc?  If you can't boot from a CD then you can't ever install Windows from scratch again....

If another CD boots but Ubuntu does not THEN you know that the disc is bad...

---

### Post by Spyware on 2005-09-13
yes i inserted win2000 cd and it boots after i deleted windows

so it seems that is something wrong with ubuntu

---

### Post by aysiu on 2005-09-13
[QUOTE=Spyware]
so it seems that is something wrong with ubuntu[/QUOTE] Or your CD. Did you do a checksum? Did you burn it at a slow speed? Did you burn it as a disk image?

---

### Post by Spyware on 2005-09-13
[QUOTE=aysiu]Or your CD. Did you do a checksum? Did you burn it at a slow speed? Did you burn it as a disk image?[/QUOTE]


i burn it as image

at low speed several times

how to do checksum on win2000, maybe there is simple program?

---

### Post by aysiu on 2005-09-13
[QUOTE=Spyware]
how to do checksum on win2000, maybe there is simple program?[/QUOTE] You mean something like this?

[http://www.irnis.net/soft/acsv/](http://www.irnis.net/soft/acsv/)

Google works wonders.

---

### Post by Spyware on 2005-09-13
yah the problem was corupt download

now i am instaling ubuntu ;)

so time to play  ;-) 


thanks for all suport

---

### Post by GreyFox503 on 2005-09-14
I was actually suprised that your download was corrupted.  Whenever people are trying to fix problems installing Ubuntu, those three suggestions that aysiu gave are always brought up.  However, I've never had one of my downloads fail a checksum or knew anyone else's did.

In theory these kind of things can happen, but many of us (including me) have never experienced it.

Same goes for the "burn at slow speed" check...

Of course, not burning the .iso as an image is a more common culprit  :smile:

Glad it was something simple like that.  Hope you like Ubuntu.

---

