---
title: "Problem integrating HP 2575 All-in-one printer/scanner"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by David Jenkins on 2007-04-25
This is a bit of a noobie question, so please forgive me...

I have just moved over from Mandriva to Feisty with almost total success, apart from getting my HP Photosmart 2575 all-in-one printer/scanner to work properly. This device is connected to my home network (i.e. not directly connected to the PC).

I have set it up as a new printer, and it functions correctly in that role.

I cannot find its scanner when I run XSane, so obviously the drivers are either not installed or not found.  This used to work correctly on this machine in Mandriva so the principle is sound, even if the implementation is suspect!

I also have HPLIP installed, but I can't find any mention of it in the system - how do I set it up to run?

System details: 
Ubuntu version = feisty, AMD64 version
Processor = AMD64

All help appreciated...

cheers,
David

---

### Post by mikeyphi on 2007-04-25
[http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)
for instructions to install HPLIP

---

### Post by David Jenkins on 2007-04-25
Been there, read those instructions.  Unfortunately it's not that easy, as the HPLIP installation script is having trouble coping with this UBUNTU release. 

However, I just tried the manual option in the script - that does seem to have worked, but it's a bit esoteric.

It looks like the Synaptic Package Manager doesn't do a good job of installing. Shame, as the script  is a pain  :(

cheers,
David

---

### Post by mattdee on 2007-05-02
I did a search in Synaptic and found Gnome scan utility...works good!

---

### Post by ashz on 2007-05-30
hplip comes on feisty as default u just dont see it on the menus...


follow my advice on...


[http://ubuntuforums.org/showthread.php?t=438036&highlight=2575](http://ubuntuforums.org/showthread.php?t=438036&highlight=2575)

cheers
ash

---

