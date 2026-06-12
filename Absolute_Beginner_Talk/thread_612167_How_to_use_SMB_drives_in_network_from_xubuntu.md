---
title: "How to use SMB drives in network from xubuntu"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by popch on 2007-11-13
In (plain) Ubuntu with Gnome, I can easily browse and attach SMB drives in my LAN, such as those shared by Windows machines.

How do I do that from Xubuntu (7.10) ?

---

### Post by zabien1970 on 2007-11-13
STOP Read top sticky first

---

### Post by popch on 2007-11-13
Thank you. Please consider first sticky read. I am not going to remove my directories. 

Now, how do I browse and use SMB with Xubuntu?

---

### Post by buntunub on 2007-11-13
What they mean is:

Samba
Samba is a fileserver you can install in Ubuntu. It's quite hard to install and configure it properly. Once it's working it's an easy way to share files between computers in a trusted network (such as your house).

The Samba part of the official server guide
[https://help.ubuntu.com/ubuntu/serve...etworking.html](https://help.ubuntu.com/ubuntu/serve...etworking.html)

Ubuntu Documentation: Setting up Samba
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

HOWTO: Setup Samba peer-to-peer with Windows
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

Samba Homepage
[http://samba.org/](http://samba.org/)

Samba documentation on the samba website
[http://us3.samba.org/samba/docs/](http://us3.samba.org/samba/docs/)

The Official Samba-3 HOWTO and Reference Guide
[http://us3.samba.org/samba/docs/man/...TO-Collection/](http://us3.samba.org/samba/docs/man/...TO-Collection/)

Practical Exercises in Successful Samba Deployment
[http://us3.samba.org/samba/docs/man/Samba-Guide/](http://us3.samba.org/samba/docs/man/Samba-Guide/)

Using Samba, 2nd Edition
[http://us3.samba.org/samba/docs/using_samba/toc.html](http://us3.samba.org/samba/docs/using_samba/toc.html)


Read through all those threads then come back if you still dont understand. Bear in mind that Linux is NOT windows and therefor support = zero. Xubuntu is NOT for noobs. Ubuntu is. Xubuntu and XFCE are not nearly as user friendly as is GNOME and KDE, however it is a far superior window manager to either of the other two for a multitude of reasons. Once you get the hang of how things work, there simply is nothing better. Have fun learning and never stop!

---

### Post by popch on 2007-11-14
> **buntunub said:**
> 
Samba is a fileserver you can install in Ubuntu. It's quite hard to install and configure it properly. 

Thank you very much for your references.

However, being a beginner (and this being the place for beginners), I am stumped by something much simpler:

How do I set up the Xubuntu box as a samba ***client***?

To reinforce from the first post: In plain Ubuntu (Gnome) there is Places->Servers and Places->Network which lets you find shared volumes in your LAN and attach them to your desktop. I can not find that function in Xubuntu's desktop.

---

