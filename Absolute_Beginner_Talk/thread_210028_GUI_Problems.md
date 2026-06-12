---
title: "GUI Problems"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by saaboycl on 2006-07-06
Hello, I am having problems with viewing the GUI side of Ubuntu.  I have an Aopen AK73 PRO(A) mother board with an AMD Athlon Duron & T-Bird Socket A 200Mhz DDR processor.  The video card is model: vidpci009abww stb trio64v pci.  I'm trying to run the live cd, and when it gets all the way through the installation my monitor goes into sleep mode like it is not getting any signal.  If i hit Ctrl + Alt + f4 + f6 it will bring me to a command prompt that says "ubuntu@ubuntu:~$".  I am new to Ubuntu and Linux, the only command i know is PWD and that worked.  Any suggestions of how i can get the GUI side of Ubuntu to work would be much appreciated, and please let me know if you need more information.

---

### Post by mcduck on 2006-07-06
When you start the live CD, you could try the safe graphics mode..

---

### Post by az on 2006-07-06
How much ram do you have?

Also, maybe you can try dissabling the screensaver while you install?

---

### Post by shoot2kill on 2006-07-06
sudo aptitude install ubuntu-desktop

or 

sudo aptitude install kubuntu-desktop

or 

sudo aptitude install xubuntu-desktop

---

### Post by saaboycl on 2006-07-07
I have only one 128 stick of ram, do you think this could be the problem? How do i disable the screen saver?

---

### Post by saaboycl on 2006-07-07
> **shoot2kill said:**
> sudo aptitude install ubuntu-desktop

or 

sudo aptitude install kubuntu-desktop

or 

sudo aptitude install xubuntu-desktop
I'm sorry, i'm not sure what you mean?

---

### Post by saaboycl on 2006-07-07
safe graphics mode worked! Will i need to run it in this mode always? will i have this option if I install instead of run the live CD?  thank you everyone for your feed back.

---

### Post by mcduck on 2006-07-07
the installer should configure Ubuntu to automaticly use safe graphics mode, so if everything goes fine you don't even need to think about this ever again :)

Anyway, The installer on the live-cd requires at least 256MB of RAM, so you'd better download the Alternate-CD and use that one to install Ubuntu. Alternate CD has a text-based installer that should work fine on your machine..

---

### Post by raldz on 2006-07-07
> **mcduck said:**
> 
Anyway, The installer on the live-cd requires at least 256MB of RAM, so you'd better download the Alternate-CD and use that one to install Ubuntu. Alternate CD has a text-based installer that should work fine on your machine..

I was able to manage to install from the Live CD with only 128MB of RAM.. it was damn sllloooowwwww... but it did install successfully..

---

