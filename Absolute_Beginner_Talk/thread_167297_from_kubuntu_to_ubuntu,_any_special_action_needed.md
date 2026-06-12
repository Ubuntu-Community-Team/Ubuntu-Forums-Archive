---
title: "from kubuntu to ubuntu, any special action needed?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Arandil on 2006-04-28
In an effort to start of with a new, clean system, I would like to change from Kubuntu to Ubuntu. My system consists of a dual-boot solution, with XP on my master HD and kubuntu on a slave HD. Installing Ubuntu will not cause any troubles I believe, since that will just be inserting the cd into my pc and format the slave HD. My main concern is my bootloader (GRUB). Do I have to change anything there or will this be done automatically?

---

### Post by catlett on 2006-04-28
You don't have to reinstall all you have to do is ```
sudo apt-get install ubuntu-desktop
```
This will install the ubuntu desktop, Gnome in your Kubuntu install. Then when you log on, click on "sessions" there you can choose the Kubuntu desktop (kde) or the Ubuntu desktop (gnome). 
It's as easy as that. This is how my system is (except I did it the other way, I installed Ubuntu first and added the kubuntu-desktop). You go betweeen them by logging on/off. You don't even have to restart your computer.

P.S. If you still want to reinstall, your assumptions are right. You can format the slave drive again and install to it like you did kubuntu. Grub will be reinstalled by the new installation.

---

### Post by gingermark on 2006-04-28
I believe it will be done automatically.

---

### Post by Arandil on 2006-04-28
[QUOTE=catlett]You don't have to reinstall all you have to do is ```
sudo apt-get install ubuntu-desktop
```
....[/QUOTE]

That would be a solution, and quite an easy one, that's for sure. It's just that I would like to start completely clean :) So therefore my question remains: do I have to edit GRUB? Not that it will be a wreck like that first time I tried to install a linux distro and my windows became inaccessable...

---

### Post by ajgreeny on 2006-04-28
You will not need to do anything to grub as it will still be the same kernel being used and should still boot without problems.
If you want to clean up a bit you could also remove the kde bits in your system using synaptic, or "apt-get remove".

---

### Post by beewer on 2006-04-28
edit: removed post and moved to proper place.

---

### Post by beewer on 2006-04-28
edit: removed post and moved to proper place.

---

### Post by beewer on 2006-04-28
edit: removed post and moved to proper place.

---

