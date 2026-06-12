---
title: "I accidently formatted my 2Gig flash drive. =("
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2007-12-13
When I tried to open it in Windows it says: "Not compatible with Mac/Apple format" or something along those lines. 

Would it work here in Ubuntu? Plus I need it to work on XP because I have to transfer some files from my girlfriends computer to mine.

Please help!

---

### Post by PmDematagoda on 2007-12-13
Use Gparted to format the flash drive, install Gparted using:-

```
sudo apt-get install gparted
```

---

### Post by papuccino1 on 2007-12-13
Oooh sexy program gparted. I like! Thanks for the help, I'll be back if more porblems arise with this.

EDIT: Hey quick question about the code you put there. 

Sudo= Override anything (master control) :P
apt-get = Aplication Get (retrieve) 
Installe = install
gparted = the program you want


Am I correct? I just want to get familiar with the terminal code and whatnot. 

So if I wanted to install Frostwire I would put:

sudo apt-get install frostwire


Would this work?

---

### Post by dptxp on 2007-12-13
Format it in FAT16. That is the standard for flash.

---

### Post by papuccino1 on 2007-12-13
New problems emerge!

I installed the gparted program. But I can't find it anywhere on the applications tab or anywhere. Where is the default install location?

---

### Post by papuccino1 on 2007-12-13
I used the deskbar applet to try and find it, and I did. 

But when I try to open it, it says I need "root access". I thought I was already the admin on this machine? What the heck? :P

---

### Post by FuturePilot on 2007-12-13
It should be under System>Administration>Partition Editor

---

### Post by papuccino1 on 2007-12-13
> **FuturePilot said:**
> It should be under System>Administration>Partition Editor

Ok found it. But I wonder why it couldn't open it under the Deskbar applet. :S

The program is appareantly scanning all devices but it just keeps scanning and scanning. How long does it usually take?


EDIT: Ok, it's STILL scanning so I know it's an error. What do I do know?

---

