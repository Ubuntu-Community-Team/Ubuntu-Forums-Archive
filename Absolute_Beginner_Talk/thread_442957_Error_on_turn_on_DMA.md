---
title: "Error on turn on DMA"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by AlexRat on 2007-05-14
Hi!
I want enable DMA on my computer.
When I make command "hdparm -d1 /dev/cdrom", I have error:

/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

How can I solve this problem???

---

### Post by alienexplorers on 2007-05-14
Try  

> sudo hdparm -d1 /dev/cdrom

---

### Post by AlexRat on 2007-05-14
10x, but I usually used "sudo su" and after this execute all commands that need root privileges.
I means
> $sudo su
#hdparm -d1 /dev/cdrom
is equivalent of
> sudo hdparm -d1 /dev/cdrom
Isn't it?

---

### Post by Nameless_one on 2007-07-11
Hi, I am having the same problem. I have noticed there are several threads and tutorials on how to overcome this here and in other communities, however, I have been able to follow none. The reason is that the most commonly syggested solution is that I must add a module which depends on my motherboard to the /etc/modules file, **before** another module, ide-cd. 

However, ide-cd isn't in the modules list, but when I run lsmod, it appears, which I think means is loaded automatically from somewhere else, before the /etc/modules list is even read, so there is no way for me to have amd74xx (which I think is the right module for my chipset) to be loaded before ide-cd. 

Or maybe you can help me :)

EDIT: Just a little bump :)

---

### Post by Nameless_one on 2007-07-11
Just bumping.

---

### Post by Nameless_one on 2007-07-11
Noone, eh?

---

