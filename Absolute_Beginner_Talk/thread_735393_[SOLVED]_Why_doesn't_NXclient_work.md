---
title: "[SOLVED] Why doesn't NXclient work?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by A$h X on 2008-03-25
Okay, I'm not a compete noob when it comes to networking, I've setup a home network of 2 XP machines and my ubuntu box, everything works okay (XP can see/access ubuntu and vice versa).
I've installed NXclient on all machines, and opened a port for NXclient, but when I run it, I get the dreaded (and not very precise) "connection refused" error. I've specified what I assume are the correct static IP addresses (192.168.1.x) and the port I forwarded in my router (even though this is over my LAN so I don't think I need to open that port).
Could someone please point me the right direction? I've tried NXclient on both my ubuntu and XP machines and it seems to be no-go. Any help is gratefully received.

---

### Post by dwanders on 2008-03-25
I am sure this is a silly question, but you did download and install the NXServer on your Ubuntu computer first correct? So your plan is to run the NXServer on Ubuntu and access it with the NXClients from Windows. (I have never done this, but I am going to go home and set it up on my home LAN this eventing if time permits - I have always wanted to see how this stuff works).

---

### Post by A$h X on 2008-03-25
Yes I have, but apparently it's important to install the NX programs in a specific order: Client, Node, Server.
On the windows machine (the machine from which you will be "controlling" ubuntu) you only need NX client. I'll try uninstalling the apps from my ubuntu box and installing them in the right order.

---

### Post by A$h X on 2008-03-25
Looks like there's lots of tampering to be done with nxserver in the terminal. I was hoping for a minimum of configuration and thought it was meant to work pretty much out of the box. I have logged into testdrive no problem, but logging into my machines seems to be very difficult. Any nxserver users out there who can help me out?

---

### Post by A$h X on 2008-03-26
Well, I got NXclient working :) After trawling through the admin guide and tinkering with my setup I finally got my ubuntu desktop to appear in a window on one of my XP machines! It's so fast your could fool yourself into thinking you were physically sitting at and using the linux machine! 
If anyone wants I could write up a quickstart guide to using NXclient/server on ubuntu and XP. Now the next step is to get my XP desktop to virtualize onto my ubuntu desktop (tightVNC here I come...)

---

### Post by kpkeerthi on 2008-03-26
> **A$h X said:**
> Well, I got NXclient working :) After trawling through the admin guide and tinkering with my setup I finally got my ubuntu desktop to appear in a window on one of my XP machines! It's so fast your could fool yourself into thinking you were physically sitting at and using the linux machine! 
If anyone wants I could write up a quickstart guide to using NXclient/server on ubuntu and XP. Now the next step is to get my XP desktop to virtualize onto my ubuntu desktop (tightVNC here I come...)

Great.

Feel free to contribute a HOW-TO in the [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100") section. Someone in need for it can find and use it even if they miss this thread.

---

