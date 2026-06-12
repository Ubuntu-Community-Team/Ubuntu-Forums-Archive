---
title: "Reassignment of Printer IP Port"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-02-14
Yesterday I updated my system to the newest Ubuntu Kernel.  Suddenly printing on my network from my WIN2k box through this Ubuntu machine (6.1) was no longer functional. 

It seems that my inet IP address for my printer was changed.  

Is this normal behavior in Ubuntu/Linux when kernels are updated or was this caused by something else?

---

### Post by go2dell on 2007-02-16
Is this a printer either with a built-in print server, or possibly connected to an external print server box?  Or is the printer connected directly to your PC?

In short, the kernel upgrade shouldn't have anything to do with any IP address, either on your computer or elsewhere.  If your printer is using either an internal or external print server, then my first thought would be to check elsewhere before looking at your PC.  If your printer is connected directly to your PC then it's obviously where you should start looking.

The Ubuntu Server manual may be of some help to you as you look for what changed so you can change it back.  Specifically, look at the sections on Network Configuration and TCP/IP in the [Networking section]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/networking.html") of the manual.

---

### Post by chaplanger on 2007-02-17
go2dell,
This printer is directly connected to my Ubuntu machine and is shared over a wireless network with my WIN 2k box.  

Something simply changed the IP address of the printer.  By changing the IP to be addressed by the WIN 2k box, I am back up and running.  Some weeks ago a similar situation occurred in which my WIN 2k could not connect to the printer (I'm beginning to wonder if it was the same situation) hmmmm. . . . I'll have to keep a close eye on this.

I wonder if the development team has ever run into any such situation.

---

