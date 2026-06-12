---
title: "Local disk &amp; wireless connection"
date: 2005-06-06
forum: Absolute Beginner Talk
---

### Post by aapje on 2005-06-06
Forgive my ignorance, but how do I access my local harddisc? Clicking Computer//Filesystem brings up all kind of maps which bare no resemblance to the explorer view when using Microsoft Windows. I was not able to locate any of my audio or document files.

Also, how do I set up a wireless connection connecting my computer to my DSL access point (enter encryption, etc). Do I need additional software to set this up?

I'm using the live edition.

Thanks.

---

### Post by somuchfortheafter on 2005-06-06
that is because that is the linux file system not yours, try this
```
 sudo mkdir /windisc 
```
```
sudo mount /dev/hda1 /windisc 
```
btw when prompted for a password just hit enter
then finally
```
nautilus --browser /windisc 
```

if you get  no error messages that should do it for ya.

---

### Post by aapje on 2005-06-06
[QUOTE=somuchfortheafter]that is because that is the linux file system not yours, try this
sudo mkdir /windisc
sudo mount /dev/hda1 /windisc
btw when prompted for a password just hit enter
then finally
nautilus --browser /windisc

if you get  no error messages that should do it for ya.[/QUOTE]

So, where do I enter that stuff?  :roll:

edit: isn't it possible to access the windisc easily, without typing all that code (just clicking the mouse)?

---

### Post by somuchfortheafter on 2005-06-06
ok the disk isnt "mounted by default" sorry this is one of the many so called faults of linux but if you think about it there is no real need for a system to mount every drive all the time especially when they are not used, however for hd install users a simple file edit corrects this, but so sorry you are stuck with the commands on the live cd and when changing that file.
so where do you enter the commands you ask
right click anywhere in a black area of the desktop and select open termina, once that opens enter in the commands. also if you would open another terminal and type in ```
 ifconfig 
``` that would be very helpful to all of us when we get to your wireless card.

---

