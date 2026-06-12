---
title: "Create a .ISO  Backup"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-28
Hi All

 Is it possible to write an image .ISO file  to disk or USB or CD with Ubuntu?

This if possible would provide a backup copy of my system.

Thanks for any help

---

### Post by dude of wonders on 2006-02-28
i'm pretty sure gnomebaker does that, if you don't already have it you can get it from synaptic package manager. i think it only does cd and dvd images though.

---

### Post by codejunkie on 2006-02-28
[QUOTE=kent41]Hi All

 Is it possible to write an image .ISO file  to disk or USB or CD with Ubuntu?

This if possible would provide a backup copy of my system.

Thanks for any help[/QUOTE]
yep they make it pretty easy to make an .iso file in ubuntu. open up nautilus and enter```
burn:///
```move all the files that you want in there, click the Write to Disc button, it will open a prompt in the drop down box choose File Image and it will create a .iso file for you.

---

### Post by kent41 on 2006-02-28
[QUOTE=codejunkie]yep they make it pretty easy to make an .iso file in ubuntu. open up nautilus and enter```
burn:///
```move all the files that you want in there, click the Write to Disc button, it will open a prompt in the drop down box choose File Image and it will create a .iso file for you.[/QUOTE]

Ok the next question  you say move all the file into the disk writer. Can I take the   .ISO file and write it to a clean hard drive and boot ?

Synapitc says I have nautilus installed but I don't know how to get to it.

---

### Post by codejunkie on 2006-02-28
[QUOTE=kent41]Ok the next question  you say move all the file into the disk writer. Can I take the   .ISO file and write it to a clean hard drive and boot ?[/QUOTE]
no it wont boot, if your talking about imaging your whole drive and burning it to cd/dvd, you'll most likely run into permisssions problems restoring the files and have a big mess on your hands. i thought you were just talking about backing up your data not the whole os. there was a howto on here on how to backup and restore your entire system that might do what your looking for just search the howto sections.

---

### Post by dvarsam on 2006-03-01
Read the Article#: 137276

---

### Post by mdsmedia on 2006-03-01
ok, silly question.... where in nautilus do I enter any sort of command?

---

### Post by kent41 on 2006-03-01
Ok I get it now.

And for all you others who can't find nautilus including myself.

Click on PLACES>COMPUTER this is nautilus !

---

### Post by daredevil on 2006-03-01
Found this in tips and tricks section

Open up a terminal window into this window type: dd if=/dev/cdrom of=$HOME/cdrom_image.iso

I'll now explain what this all means in the key below

dd - disk duplicate
if - input file
of- output file
$HOME - system variable that points to your user directory.

Ps:Change cdrom_image to what ever you want the iso to be called.

---

### Post by kent41 on 2006-03-01
[QUOTE=daredevil]Found this in tips and tricks section

Open up a terminal window into this window type: dd if=/dev/cdrom of=$HOME/cdrom_image.iso

I'll now explain what this all means in the key below

dd - disk duplicate
if - input file
of- output file
$HOME - system variable that points to your user directory.

Ps:Change cdrom_image to what ever you want the iso to be called.[/QUOTE]
Thanks daredevil
what can I do with the .ISO file ? How do I get this .ISO image to my hard drive and then boot from it ?

---

### Post by theturner on 2006-03-01
[QUOTE=mdsmedia]ok, silly question.... where in nautilus do I enter any sort of command?[/QUOTE]
Press Ctrl+L (as in _L_ocation), then enter the path.

---

### Post by kent41 on 2006-03-01
Daredevil

I am confused the command

```
dd if=/dev/cdrom of=$HOME/cdrom_image.iso

```

In this command the input file is a cdrom.
How did the system get to a CD?

Let me start over.
What I want to do is simple I think, Make a backup of current Ubuntu OS and transfer it to a different Hard drive so if the current system gets corrupt I can take the corrupt disk out of my computer and install the backup hard drive in my computer. As I mention before i have spent many hours installing applications and to me it makes sense to not have to go thru all the hours of re-installing apps. If Ubuntu was more stable when we add apps. bad things would not happen there maybe would not be a need for a OS backup. However just look at the threads. If we were more knowledgable with linux this would not happen. But the facts speak for themselves the threads have one overiding theme FRUSTRATION.

If this is not possible Please just say its not possible and I will go on to something else. 

All I would like is to backup a hard drive to install in my computer if the current one gets corrupt.

---

### Post by dvarsam on 2006-03-01
Hello, I understand your concerns.

Read Article#s: 136195 & 136939

Hope they help.

---

### Post by tadashi on 2006-03-01
Can you give the links of where to search for those article #'s?  I am still learning linux and have managed to break mine 8 times.  On the bright side I now how the instllation and configuration down to 3.5 hours. :p  Burning a CD image of my linux partition would be a lot easier to fix my mistakes. :KS

---

### Post by dvarsam on 2006-03-01
Well, if you go up in your Mozilla Firefox to read the address of THIS article, you will read:

[http://ubuntuforums.org/showthread.php?t=137931&page=2](http://ubuntuforums.org/showthread.php?t=137931&page=2)

So this article # is: 137931&page=2

Replace this with: 136195

& you will get:

[http://ubuntuforums.org/showthread.php?t=136195](http://ubuntuforums.org/showthread.php?t=136195)

You will automatically redirected to the above article (# 136195)

If you have problems, write back.

---

