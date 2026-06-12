---
title: "Need help with network driver"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by realizee on 2007-10-29
Hi  ,
I wonder if any u guys know how to install or start my network driver? 
SiS 900 PCI Fast Ethernet. I dont know on which eth it is. 
So i'm a real beginner please respect and answer

---

### Post by skymera on 2007-10-29
have you tried nDiswrapper yet?

it cop[ies the .inf from the driver for windows to make your card compatible :wink:

try:

sudo ifconfig *device name* up

is it actually enabled in network-manager?

---

### Post by julian67 on 2007-10-29
> **realizee said:**
> Hi  ,
I wonder if any u guys know how to install or start my network driver? 
SiS 900 PCI Fast Ethernet. I dont know on which eth it is. 
So i'm a real beginner please respect and answer

This interface's driver shouldn't need installation, it's part of the kernel and should just work.  It does for my Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91).

Did you try to use it?

---

### Post by realizee on 2007-11-01
I'm really new with this ubuntu but i have a network on the upper menubar. and everytime i login to my account i gotta click on the network icon and choose a network between 3. the other two doesn't seem to work i don't know.. :P PLEASE HELP.

---

