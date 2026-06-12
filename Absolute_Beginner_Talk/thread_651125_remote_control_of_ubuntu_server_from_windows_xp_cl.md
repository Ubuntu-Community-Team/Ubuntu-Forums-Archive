---
title: "remote control of ubuntu server from windows xp client"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by ingvald on 2007-12-27
Have read several how to's on this subject. 

I only have one question:
Will running Putty (SSH client for windows OS) give you GUI connection to your Ubuntu box at home (Given you've installed a SSH server, configured it to listen to the right port, forwarded the port on your router and properly set up DynDNS account)? Sound and all?

So with other words I want to remote control my ubuntu edgy laptop at home as I was sitting right in front of it. WIth full GUI.

another question: 
any suggestions for ways to remote control your home ubuntu server from everywhere in the world...if I am travelling f.ex? Portable client on a usb drive?? 

Is the secure way to go: ssh client for windows, ssh server, portforwarding and DynDNS?

---

### Post by blueridgedog on 2007-12-27
> **ingvald said:**
> Will running Putty (SSH client for windows OS) give you GUI connection to your Ubuntu box at home (Given you've installed a SSH server, configured it to listen to the right port, forwarded the port on your router and properly set up DynDNS account)? Sound and all?


No.  SSH is a text based way of managing a server.  However, you can tunnel other protocols over it, but that is another story.

To get the full GUI, you will need to either use VNC (my recommendation - and the same list of to-do's that you have above apply) or to install an X server (yes server) on your XP machine so that applications on your Ubuntu box can export their display to the remote X server onyour XP system.

I would try VNC first.

another question: 
any suggestions for ways to remote control your home ubuntu server from everywhere in the world...if I am travelling f.ex? Portable client on a usb drive?? 

The VNC client will fit on a USB key and can be run from most any system, you could even keep clients for Linux and windows on the USB key.

---

### Post by blueridgedog on 2007-12-27
Also, you could look into the Linux Terminal Server Project:

[http://www.ltsp.org/](http://www.ltsp.org/)

---

### Post by ingvald on 2008-01-05
Since I want to have a full GUI I will try the VNC first as you recommends. But is this secure? I need some kind of encryption to protect my connection and data that I want to have access to in remote control. My ubuntu "server" will be running 24/7 so I really want to be sure my remote connection to it is reasonable safe. I am newbie and dont know much about linux, so if there is some easy guides out there or people that can give me some good words about this I will really appreciate it.

I have searched around and I have the impression that VNC is not secure....if so...I am back to where I started I think. Looking for a secure, encrypted way of remote control of my computer.

When I used windows  I did this using LogMein (which they claimed to be encrypted) Worked very nice....

---

### Post by blueridgedog on 2008-01-05
Take a look at:

[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

### Post by Dr Small on 2008-01-05
You can port VNC over SSH, but that's now how I'd do it:
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

I'd connect to the system with SSH and port the desktop (not really a remote desktop, but rather the GUI or WM) over to the pc I am sitting at. For Windows XP, I would recommend Xming:
[http://freedesktop.org/wiki/Xming](http://freedesktop.org/wiki/Xming)

 For Ubuntu, I would recommend Xephyr:
[http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)

---

