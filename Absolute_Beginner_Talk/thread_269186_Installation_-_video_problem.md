---
title: "Installation - video problem"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Mqoqobeli on 2006-10-01
A few months ago I tried to install the Breezy version of Ubuntu. I have heard a lot about Ubuntu and was excited to try it out. After the installation process the computer restarted - but then the screen turned black (no display). There seems to be a problem with the video drivers.

Here are some of my computers specs:
1.90 gigahertz AMD Athlon XP
NVIDIA GeForce FX 5200 [Display adapter]
NVIDIA NForce MCP2 IDE Controller

I have never used linux before - so I'm a complete beginner. How can one fix this problem if the there is no display?

---

### Post by tronica on 2006-10-01
when you get to the black screen try pressing ctrl+alt+F1 and then type

> sudo dpkg-reconfigure xserver-xorg

and just follow the steps

---

### Post by Mqoqobeli on 2006-10-01
Thanks. I will try that next time I install.

---

### Post by Mqoqobeli on 2006-11-11
Today I tried to install the new Ubuntu 6.10 version. When I booted the CD the following happened:

1. I selected option 1 (install Ubuntu)

2. After this the Ubuntu logo displayed and I could hear something was loading

3. After about 1 min my computer monitor turned off

4. I then heard a Ubuntu startup sound, but the monitor did not turn on again

5. After many minutes of wait (nothing happened) I tried to do what tronica told me in his post: 

> **tronica said:**
> 
when you get to the black screen try pressing ctrl+alt+F1 and then type
sudo dpkg-reconfigure xserver-xorg
and just follow the steps


I did this but got the following error message:
conflicting actions -e (--control) and -r(--remove)

I am not sure what to do now.

I would really like to get Ubuntu installed on my computer. Will appreciate any help.

---

### Post by ReaderRat on 2006-11-11
Try indtalling in 'Safe Graphics Mode' (on the LiveCD boot menu) to see if you can get set up with a Vesa driver for your monitor. You can configure your graphics card later.

---

### Post by Mqoqobeli on 2006-11-12
I tried the 'Safe Graphics Mode' but still got the blank screen. I searched the forum for "blank screen" and discovered that others with Nvidia display cards have had similar problems. Is this a bug in Ubuntu? I have never accoutred this problem with other Linux distributions. Wonder why it has not been fixed, since I have never been able to install any Ubuntu version on my computer.

I tried to follow some of the advice I found on the forum, like:

1. Editing the /etc/X11/xorg.conf and changing Device: "Visa" to Device: "nv"

2. Trying to change the screen resolution with ctrl-alt and +

3. Running "sudo dpkg-reconfigure xserver-xorg" and reconfiguring

But could not fix the problem

Must again mention that I am a complete Linux beginner.

---

### Post by ReaderRat on 2006-11-12
You may have already googled this. You have to subscribe to the Board there to view the solution....I did not want to do that...
**[http://www.experts-exchange.com/Operating_Systems/X_Windows/Q_21645495.html](http://www.experts-exchange.com/Operating_Systems/X_Windows/Q_21645495.html)**
I will keep looking for a while.

---

### Post by Mqoqobeli on 2006-11-15
Thanks for the help. I saw that one has to pay to subscribe to the board you mentioned - which I'm not going to do. Looks like I'm in a stalemate now.

---

### Post by Mqoqobeli on 2006-11-20
Is it possible to report this error to the developers of Ubuntu? Many users with the NVideo Video card has this problem.

---

