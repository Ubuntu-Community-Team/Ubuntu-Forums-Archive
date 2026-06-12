---
title: "troubleshooting cd burning"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by dascheer on 2007-07-09
whenever i open serpentine i get this error message:

"No recording drive found

No recording drive found on your system, therefore some of Serpentine's functionalities will be disabled."

I can't burn cds on my computer -- and ive tried k3b and other programs too.  what packages/code do i need.

---

### Post by sailor2001 on 2007-07-09
you have no writer drive (not cd-rom) in your computer?     Or is it that it doesn't read the disk you put into the drive?  Also have you tried devede (synaptics) or gnome baker?

---

### Post by dascheer on 2007-07-10
i have a cd burner; its not just bruning mp3s.  i was able to burn oggs in the past, but i dont use that format

---

### Post by mytwobears on 2007-07-10
I think it may be a codec issue.  Make sure you have the correct codec that will allow you to burn mp3s.  Maybe lame or etc.  Sometimes one codec will allow the program to read it but you need another version to burn it.  Also, you have to make sure that Serpentine knows where the codec is, that is, you have to tell it where it is.

---

### Post by dascheer on 2007-07-11
i downloaded all the codec packages and their libraries i could find, including mad and lame.  nothing still works.

---

### Post by ramjet_1953 on 2007-07-11
Copy and paste this command into a terminal:

[COLOR="Red"]wodim --devices[/COLOR]

You should get something like this:

r[COLOR="Blue"]oger@roger-laptop:~$ wodim --devices
Beginning native device scan. This may take a while if devices are busy...
wodim: Overview of accessible drives (1 found) :
----------------------------------------------------------------------
0    dev='/dev/sr0'   rwrw-- :  'MATSHITA'  'UJDA760 DVD/CDRW'
----------------------------------------------------------------------
roger@roger-laptop:~$ [/COLOR]


The post the output back to this forum.

Regards,
Roger :cool:

---

### Post by dascheer on 2007-07-13
danny@momo:~$ wodim --devices
Beginning native device scan. This may take a while if devices are busy...
wodim: Overview of accessible drives (1 found) :
----------------------------------------------------------------------
0    dev='/dev/sr0'   rwrw-- :  'Optiarc'  'DVD+-RW AD-5540A'
----------------------------------------------------------------------
danny@momo:~$       


thanks for the help!

---

### Post by cogumbreiro on 2007-08-13
Does Nautilus work for you? Serpentine uses the same library for writing CDs.

---

