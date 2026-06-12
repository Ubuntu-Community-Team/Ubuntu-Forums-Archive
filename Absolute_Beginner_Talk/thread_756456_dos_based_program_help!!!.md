---
title: "dos based program: help!!!"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by alpdo on 2008-04-15
i have my ubuntu gutsy box used as file server and placed on it a dos based program which i run on my network... but every time i run my program it say general failure reading drive d:
what should i do????
i keeps appearing everytime i run my program:confused:

---

### Post by spiderbatdad on 2008-04-15
Most likely a permissions problem accessing the file system. I would guess you need to determine what files are being accessed and chmod them.

---

### Post by alpdo on 2008-04-15
i used my program on a win98 os and win xp .... on my windows xp no problem but on my win98 it runs fine on first run... but on the second it says general failure reading drive....

---

### Post by neurostu on 2008-04-15
How again are you running a DOS program in Linux? You shouldn't be able to run a native DOS program in Linux... Are you using some sort of virtualization or wine?

---

### Post by alpdo on 2008-04-15
i copied my progrom to my ubuntu shared folder and i run my program from my win98 and win xp pc

---

### Post by mgmiller on 2008-04-15
I don't know if this will work, but from the windows machines could you try mapping the network drive you are sharing on Ubuntu as drive D:  Then access the program through that mapped share.

---

### Post by alpdo on 2008-04-15
i already did that i did not work

---

### Post by mgmiller on 2008-04-15
Try reading up on dosemu.  Here is a quote from wikipedia:
> the ability to provide DOS services through native Linux services; for example, dosemu can provide a virtual hard disk drive which is actually a Linux directory hierarchy.
This sounds like what you may need.
The packages are in synaptic
dosemu
dosemu-freedos

[http://www.dosemu.org/]("http://www.dosemu.org/")

---

### Post by alpdo on 2008-04-15
my program was created on foxpro 2.6 ....  everytime i run it from my windows 98 pc it says ... general failure reading drive....

---

### Post by neurostu on 2008-04-16
Does it run in winXP?  I'm not sure if this will make a difference, but win98 used the fat32 file system where as winXP used NTFS.  If your program was written with winXP in mind I imagine that it isn't backwards compatible.

---

### Post by alpdo on 2008-04-16
yes it runs find on win xp but not on win 98

---

### Post by neurostu on 2008-04-17
It probably is reliant upon the NTFS file system which doesn't exist for windows 98.

Are you having problems running this program in Linux or in Windows 98?

This is a linux support forum, If your having problems running it in windows I would suggest finding a windows support forum or contacting the provider of the application for further support.

---

### Post by |{urse on 2008-04-17
eww @ foxpro! I used to support that program back in the day (sorry no help on that but seeing foxpro was a blast from the past) :lolflag:

edit: thinking about that the only way i can see that working is a ntfs partition nfs mounted maybe? regardless looks like you make something that belongs on windows. What does the app do?? is it tiny? perhaps you could rewrite it in C?

---

### Post by alpdo on 2008-04-17
tanks for all the help maybe theres ... i have tried using a vfat partition... its the same error...
the program since is was written in dos i think i could try to write in c... tanks...

---

