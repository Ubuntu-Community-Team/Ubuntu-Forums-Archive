---
title: "Internet problem?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by mallama on 2006-12-31
Okay, I am new at this so bare with me. I am very interested in giving ubuntu a try. Everything installed just fine but this is my problem, I have DSL with one Windows XP computer setup with ICS on it with a PPPoE dialer. I have a linksys router setup as a switch/wireless access point for my other pc's, which one is xp and the other is a laptop running ubuntu now. I have tried using the ethernet card and the wireless card both don't seem to let me online. I have also tried setting my ip address manually. Is there a problem with using ICS with a unix based system/ubuntu?  Thanks for the help! 
Cheers

---

### Post by jonathan.lees on 2006-12-31
Have you made sure you have the correct default gateway set?

---

### Post by mallama on 2006-12-31
Ok cool it started working. So everything is ok. So know i know you can use windows ICS with a ubuntu system! My next question is how do you open a shell to type commands? Is that the same as a terminal? And how to you change to the root user in a shell so you can run administrative commands? Thanks everyone for the help!! This is great. I just need to get my wireless working and ill be the happiest guy in the world. I am going to try and use ndiswrapper..... Thanks for all the help and with me good luck :) 

CHEERS!


ps. also how similar is ubuntu to redhat? It seems that ubuntu just uses gnome and not KDE? Is that the difference?  Is this a true statement? Thanks again!

---

### Post by Sef on 2006-12-31
> My next question is how do you open a shell to type commands? Is that the same as a terminal?

Yes you can type commands from the terminal.

> And how to you change to the root user in a shell so you can run administrative commands?

Use sudo before the command.  Example to use fdisk -l, type ```
sudo fdisk -l
```.  It opens up a temporary root.  Root is not enabled by default.  Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo") to find out more.

> also how similar is ubuntu to redhat? It seems that ubuntu just uses gnome and not KDE? Is that the difference? Is this a true statement?

Yes, Ubuntu uses Gnome.  Kubuntu uses KDE.  Ubuntu and Redhat use different package managers: Ubuntu uses .deb; Redhat uses .rpm.  For more information, read [Psychocat's Installing Software]("http://www.psychocats.net/ubuntu/installingsoftware").

---

