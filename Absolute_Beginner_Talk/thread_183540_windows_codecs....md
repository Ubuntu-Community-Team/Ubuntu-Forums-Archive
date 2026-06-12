---
title: "windows codecs..."
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by Niranjan81 on 2006-05-28
am trying to install the w32codecs .....for the command :

sudo dpkg -i w32codecs_20050412-0.4_i386.deb
 i am getting this message : "dpkg: status database area is locked by another process"

what do i need to do??

---

### Post by andrecasteliano on 2006-05-28
To close 'Synaptic' or 'gnome-app-install' or 'update-manager' or anything else like that :)

--
André Casteliano

---

### Post by lukew on 2006-05-28
Hi,

Do you have synaptic package manager open at the same time or another terminal su'd in as root? It is bascially saying something else has got root lock.  Reboot your machine if not, that will unlock it.

You do you that if you add the plf repository you can get these for free and then you can do sudo apt-get install w****

I hope this helps.

Luke

---

### Post by adam.tropics on 2006-05-28
That would indicate that you have synaptic/update manager open at the same time as trying to dpkg from a command line. Close them and try again.




edit: ha! you lot type too fast!!!

---

