---
title: "Home networking help"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Venetian on 2007-09-29
Forgive me if I'm asking an oft-repeated question, but I've done some searching on the forum and some general Googling, and haven't found a simple set of documentation for this...

I have a very simple home network that consists of a Toshiba desktop computer and a Dell laptop. I installed Ubuntu on my desktop machine, which is attached via Ethernet to my wireless router, which is attached to my cable modem. The Dell machine runs Windows XP Home. 

The desktop system hosts my two printers, which I want to be able to use from the Windows machine. At this point, I don't really have any need to share files between the two machines, but may need that later. As an added wrinkle, I will probably add a new iMac running Leopard and Vista later this year.

How do I configure a simple home network that will allow me to share out the printers on the Ubuntu machine so I can use them from my Windows laptop and later from my iMac?

I am pretty knowledgeable with Windows, but I am an absolute beginner with Linux -- just wanted to get my feet wet with the OS...

---

### Post by SOULRiDER on 2007-09-29
Maybe this will help:
[https://wiki.ubuntu.com/NetworkPrintingFromWindows](https://wiki.ubuntu.com/NetworkPrintingFromWindows)

---

### Post by cursebg on 2007-09-29
Did you get the machines connected at all? 
There may be many ways to do so, but I think Samba file & printer sharing will be most suitable for you. 


Install Samba:

**sudo apt-get install samba**

Backup the configuration file:

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup

Open it:

**sudo gedit /etc/samba/smb.conf**

Read the commented lines (with a # in the beginning) and edit the file for your needs :)
Save it and restart samba:

**sudo /etc/init.d/samba restart**


Wish you luck :P

P.S. [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Print_Server_.28cupsd.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Print_Server_.28cupsd.29)

---

