---
title: "Looking for 2.6.20-13 kernel"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by frafu on 2007-05-14
Hello, 

I have problems with the actual 2.6.20-15 kernel, because it fills my syslog with repeated hd messages (a corresponding bug is already filed). (the system is a dist-upgrade from edgy) 

In my boot directory, there is also a 2.6.20-13 kernel, that does not seem to have the problem with the repeated messages. Unfortunately, it seems that the 2.6.20-13 kernel is not property installed, as there are a few services that don't run as they should (for example the nfs server). 

Can anybody please tell me in which repo I can find the 2.6.20-13 kernel, in order to reinstall it? 

It is not in the feisty repo, nor in the edgy repo, nor in packages.ubuntu.com

Thanks in advance.

---

### Post by jargoman on 2007-05-14
If you have the *-13 kernel in your /boot directory but it's not visable at boot time you need to edit your grub file with 

$ sudo gedit /boot/grub/menu.lst

unfortunaly I can't tell you exactly what to add as it depends on the exact name of your kernel and the partition of your linux installation.

One thing to note is that kernal modules available from the repos won't work with a custom kernel and you'll need to compile these yourself. ie ndiswrapper, restricted driver module. I find using a custom kernel in a debian system is more trouble than it's worth and should be avoided. Anyone is free to disagree with me because i don't know everything about linux I just know I had problems with a kernal I custom compiled in the past.

make sure when you edit the file to add a new entry and not edit the old entries so you can revert to the old kernel if something goes wrong

---

### Post by frafu on 2007-05-15
Hello,

First of all, thanks for your reply. 

> **jargoman said:**
> If you have the *-13 kernel in your /boot directory but it's not visable at boot time you need to edit your grub file with 

$ sudo gedit /boot/grub/menu.lst

unfortunaly I can't tell you exactly what to add as it depends on the exact name of your kernel and the partition of your linux installation.


My problem is not adding the entries to the menu.lst; I have already edited it on several occasions. 

In fact, what I will like to do, is download the 2.6.20-13 kernel again from its repo and install it again. Unfortunately, I cannot find it in any repo. I am hoping that somebody can tell me what repo I have to add to sources.list in order to have the *-13 kernel listed in Synaptic Package Manager. 

I cannot even find the dpkg of the *-13 in the caches on my ubuntu installation.

>  
One thing to note is that kernal modules available from the repos won't work with a custom kernel and you'll need to compile these yourself. ie ndiswrapper, restricted driver module. I find using a custom kernel in a debian system is more trouble than it's worth and should be avoided. Anyone is free to disagree with me because i don't know everything about linux I just know I had problems with a kernal I custom compiled in the past.


Thanks for the indication about the modules in relation to a custom kernel. I have not compiled any custom kernel until now. I think I don't have the necessary knowledge yet... 

Have a nice day.

---

### Post by frafu on 2007-05-28
I think that the 2.6.20-13 kernel were delivered with a Feisty Herd version. It seems that the different Herd version also are not available anymore online!?

---

