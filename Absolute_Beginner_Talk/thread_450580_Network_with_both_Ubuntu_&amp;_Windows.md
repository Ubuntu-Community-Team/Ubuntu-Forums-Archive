---
title: "Network with both Ubuntu &amp; Windows"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by jgf621 on 2007-05-21
I have two UBUNTU 7.04 machines and two Windows XP machines connected via an Ethernet Router.  Both Ubuntu PC's can access both XP machines and the Internet.  But they cannot talk to each other.  (I can ping either one from the other.)

I have installed SAMBA.  Connection to XP machines is and has been trouble free.  What am I missing?

Thanks,

Joe

---

### Post by ruy_lopez on 2007-05-21
If all you want to do is access either of the Ubuntu boxes from each other, I'd forget about Samba. Install SSH `sudo apt-get install ssh`. Then when you want to access one Ubuntu box, on the other box all you do is this

Taskbar-->Places-->Connect to Server

Chose SSH as the Service Type, fill in the hostname, folder to access, username etc. and connect. This will mount whatever folder you chose from the other box onto the desktop.

On the other hand if you want to access the Ubuntu boxes from each other, AND from the Windows box, you'll have to use samba and set it up properly. Here is how to do it:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

You'll have to choose folders to share, edit the smb.conf in each Ubuntu box, and tell which users it should allow. 

The first method with SSH does all that for you. SSH is also encrypted.

---

### Post by jgf621 on 2007-05-21
Thank you.  I found I also had to install the ssh client and server.  All is now well.:p

---

