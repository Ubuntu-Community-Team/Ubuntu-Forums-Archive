---
title: "Install CD does not run when booting"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by maxcooper on 2006-11-16
Hi everybody.

This is my first time with a linux based OS and was tring to migrate from Win XP to Ubuntu. I tried with my XP still there, with my hd formatted and with DOS and could never get the install appl to run. Should i do anything special for it to run?

Any tips??

Thanks!

Max

---

### Post by Ashrael on 2006-11-16
Have you tried BOOTING FROM THE CD? Settings for boot order are found in BIOS usualy...

ahrael

---

### Post by mush on 2006-11-16
Inside of the bios (typically accessed by pressing the delete key on the post) check for something called "boot order" or something along those lines. Make your cd-rom your first device to boot from, followed by your floppy (if you have one), and finally your hard drive (maybe labeled hd0). 
with these settings changed, then the computer should boot from the cd, and start up the ubuntu install program.

good luck

---

### Post by maxcooper on 2006-11-16
Yeap, have two CD-Roms and with neither boots, the BIOS is set to check first on the CD roms and then on the floppy, that's what you meant right?

---

### Post by maxcooper on 2006-11-16
Thats what i did, but won't go. Any clue?

---

### Post by maxcooper on 2006-11-16
I'm not sure, but it seems that the CD's won't work fully before a OS has booted, because when booting with dos from a floppy, they would appear afterwards, yet with the win xp pro CD there would be no problem.

---

### Post by mush on 2006-11-16
I would suggest that you disconnect one of those cdroms that you have connected. Keep your master drive on, and maybe even check your jumper settings and make it "master" and "slave" as opposed to "cable select"
Master goes on the end of the cable, slave on the middle.

Give that a shot and see if it boots from the cdrom then.

---

### Post by maxcooper on 2006-11-16
I've tried to disconnect one of the cdroms but never seens nothing as "cable select", do you mean i should manually select which one is master and which one slave?

---

### Post by louieb on 2006-11-16
Check this [http://puppylinux.org/wikka/BurningLinuxIsoBasics](http://puppylinux.org/wikka/BurningLinuxIsoBasics) It is not just about burning an iso it also contains more that you would ever want to know about booting a PC to a Linux install CD. BTW welcome to linux

---

### Post by maxcooper on 2006-11-16
> **louieb said:**
> Check this [http://puppylinux.org/wikka/BurningLinuxIsoBasics](http://puppylinux.org/wikka/BurningLinuxIsoBasics) It is not just about burning an iso it also contains more that you would ever want to know about booting a PC to a Linux install CD. BTW welcome to linux

Ahh ok, that might be the problem, i really don't recall how did i burn it so i'll do it again. Thanks!!!

---

### Post by Ashrael on 2006-11-17
Don't know if you know,but setting a drive to master/slave/CS is done on the rear of the drive by moving the jumper (little black thingy), usualy the setting are listed on the top or bottom of the drive...If you've never done this, it's best to take the drive out of the pc, so you can see what you are doing...

Hope all the suggestions made by me and all before did it for ya!


ashrael...

---

