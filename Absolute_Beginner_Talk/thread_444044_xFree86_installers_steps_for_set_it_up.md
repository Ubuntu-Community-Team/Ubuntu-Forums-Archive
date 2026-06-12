---
title: "xFree86 installers/ steps for set it up"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-05-15
IS there out on the WEB any compiles ready for AMD64 architecture of xfree86 software/drivers?? I am looking for a version 4.3 or higher. Maybe repositories or new sources of repositories? Maybe somebody could give a me a link of a well tested page with procedures to install these files, where includes de compilation from the source? Thxs in advance!Hola vane. Que te pense hoy. COmo estas? Que hay de nuevo chica?

---

### Post by rich.bradshaw on 2007-05-16
Why do you want this? Ubuntu uses Xorg instead of Xfree86.

---

### Post by btesec on 2007-05-16
Hello,

I would like to know if their is a graphical interface for the Ubuntu Server, I am a first comer to Linux and would like to switch over have installed Ubuntu on a server already but I am not comfortable with eh command line stuff, else going to windows again.  I must say I really like the desktop version, however i work for a Gov Department and would like to switch our servers to Ubuntu server.  Please help

---

### Post by steve.horsley on 2007-05-16
krisfrajer:
Sorry, I can't help you with XFree86. As far as I know, all the common distros stopped using it 2-3 years ago and moved to xorg instead.

btesec:
Please don't hijack other people's threads. It's not that hard to start your own.
Ubuntu server installs without a GUI by default (GUIs are for desktop machines) but you can install one with this command:
**sudo aptitude install ubuntu-desktop**
If it doesn't start straight away, then use:
**sudo /etc/init.d/gdm start**

---

### Post by btesec on 2007-05-17
> **steve.horsley said:**
> krisfrajer:
btesec:
Please don't hijack other people's threads. It's not that hard to start your own.
Ubuntu server installs without a GUI by default (GUIs are for desktop machines) but you can install one with this command:
**sudo aptitude install ubuntu-desktop**
If it doesn't start straight away, then use:
**sudo /etc/init.d/gdm start**

I apologize for the hijacking.

I tried your resommended commands but none work.  Do i use the same Server CD when i try these commands?

Thanks

---

### Post by krisfrajer on 2007-05-17
Why I need xfree86? Well I am installing my super video card (not that super) radeon 9600XT in AMD64 architecture. Well To install the drivers, I need a version of Xfree86 > 4.3 plus other software requirements... one of them is a newer version of xorg. What puzzles me is what you told me that Linux switch to xorg... maybe after all I do not have to install xfree86! I will give it a try and let you know.

---

