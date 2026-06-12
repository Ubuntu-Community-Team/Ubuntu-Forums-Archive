---
title: "virtual machine"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-04-17
ive been looking for ages for the perfect virtual machine.. i want something like parrallel desktop form mac os X mainly i want to be able to pass documents from ubuntu into the virtual machine if possible by just dragging

---

### Post by amazingtaters on 2008-04-17
Well, I don't know about getting that kind of functionality (never neede/tried it) but I'm very pleased with VirtualBox (not the OSE as it doesn't have USB support but the closed source version). It's really a full featured VM that is a breeze to use.

---

### Post by Medieval_Creations on 2008-04-17
+1 for VirtualBox.  I've used it for quite some time now and it is a very good app.  Another good app, but not quite as polished is QEMU.  I have both setup, but tend to use VBox regularly.

---

### Post by linuxlizard on 2008-04-17
do a forum search for virtualbox seamless integration. I believe that's what you want.

[http://ubuntuforums.org/showthread.php?t=433359&highlight=virtualbox+seamless+integration](http://ubuntuforums.org/showthread.php?t=433359&highlight=virtualbox+seamless+integration)

for starters, but keep in mind it may be slightly out of date as it was for edgy (about a year ago). Things are much easier to set up now I think, as long as you don't use compiz or beryl.

---

### Post by patchido on 2008-04-17
that wont do.. i cant open something saved in ubuntu in the vm

---

### Post by Medieval_Creations on 2008-04-17
> **patchido said:**
> that wont do.. i cant open something saved in ubuntu in the vm

That's not entirely true... I know in VirtualBox you can setup shared folders...  (the vm see it as a network drive)...
So you could save something there and access it from both the Host & Guest OS.

---

### Post by linuxlizard on 2008-04-17
I believe you can share any folder you want with virtualbox.

---

### Post by bodhi.zazen on 2008-04-17
To be honest, best learn a network share protocol. Samba is very easy to set up and should work out of the box. Set a shared directory on your Ubuntu (server) and mount it in windows.

---

### Post by patchido on 2008-04-17
any how to into that?? that would make it.. and also with which program should i create the vm?

---

### Post by bodhi.zazen on 2008-04-17
Sure

See this one :

[uwiki]SettingUpSamba[/uwiki]

Start with the graphical configuration sections and move to manual configuration if needed.

For virtual machines I advise Virtuabox or VMWare Server. There are alternates to those, primarily qemu, but it takes a little more effort to learn qemu.

---

### Post by Narcoblix on 2008-04-17
That is not necessarily true. If you have a Mac, then you can download a VM called Q. It uses the qemu engine, but it has a completely full featured gui, and is really simple. Even me, the ultimate noob, can use this thing. It lets you set up what are pretty much shared folders between the different OS that you may run. I really recommend it. It sounds like just what you want.:)

---

### Post by patchido on 2008-04-17
> **Narcoblix said:**
> That is not necessarily true. If you have a Mac, then you can download a VM called Q. It uses the qemu engine, but it has a completely full featured gui, and is really simple. Even me, the ultimate noob, can use this thing. It lets you set up what are pretty much shared folders between the different OS that you may run. I really recommend it. It sounds like just what you want.:)

the problem starts when i dont have a mac -.-

---

### Post by patchido on 2008-04-17
i want to use samba but i cant follow that guide too good

---

### Post by bodhi.zazen on 2008-04-18
> **patchido said:**
> i want to use samba but i cant follow that guide too good

Samba is all graphical, all point and click

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

What part did you not understand ?

---

