---
title: "Office Network with Ubuntu Server"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by rfishbook on 2007-11-21
Hey, I'm completely new to Ubuntu, but while investigating cheap and effective ways to set up a network file server for my office I came across Ubuntu Server, and it seems like the way to go. 

I'm mostly wondering if anyone can tell me if what I want to do will work. 

We currently have a dedicated NFS (running Windows 2000... and working poorly) with three separate hard drives. We don't use RAID as we mostly just use it to store files for transferring ease, and so the whole office can use one HP LaserJet printer. Most of the computers connect using ethernet (run through a ridiculous and annoying amount of routers), but some are wireless through a DLink wireless G router.

In December, we'll be upgrading 6 of our workstations with new Mac Mini's (running OS X Leopard and with built in wireless), but keeping 6 of our current Windows XP workstations and purchasing TrendNet wireless USB adapters to get rid of some of the ethernet mess (I thought about installing Ubuntu on all of the workstations, but we're completely reliant on Adobe Creative Suite) .  

I'm hoping that by installing Ubuntu Server on the server, attaching the printer via standard print cable, and connecting it to the router via ethernet; all 12 computers (both Mac and PC) will have smooth and efficient wireless access to the files on the network and use of the printer.

Is this possible? 

If anyone has any experience or insight into a system setup like this it would be very much appreciated.

---

### Post by jonandrews on 2007-11-21
I've put a simple guide to integrating Ubuntu PC's into a wired Windows home network 

onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

Although this guide was not put together with a Ubuntu server in mind, it still might be helpful to your project

Let me know if it is helpful.

---

### Post by newlinux on 2007-11-21
Yep. This is all possible. You just might want to double check and make sure you HP laserjet is supported, but HP printers generally are well supported in Linux so that probably won't be a problem.

At home i have a mixed Linux/Mac OS X/Windows environment and have one primary fileserver that does exactly what you are describing, share an all-in-one printer, a laserjet, and an inkjet and serving files up via SAMBA/CIFS. Works fine, and didn't really take that much to setup. 

If you already have everything setup to use NFS, than it would probably be even easier.

One thing to give thought to is the filesystem of your drives. I'm betting they are currently NTFS... You might want to consider a different filesytem, depending on the types of files you are serving...

---

### Post by rfishbook on 2007-11-22
Thanks for the guide, it will definitely be helpful. And I will most certainly look into switching our filesystem, any suggestions on the best file system to use? I've only ever worked with NTFS and Mac extended.

Also if anyone knows of any beginner friendly guides to setting up an Ubuntu server and can post them, that would be great. I've found a few, but for the most part I end up referring to other guides every few steps to figure out how to do what they're telling me to do.

---

