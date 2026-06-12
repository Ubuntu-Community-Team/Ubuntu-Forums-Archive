---
title: "Samba Woes"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by YuHoo on 2006-03-22
I'm trying to utilize Samba in my network. I have 3 Win2k/WinXP, my linux dedicated laptop, and my brother's mac laptop. I have used Synaptic to install Samba. The problem I am having is with the console networking. Whenever I try to use smbclient to connect I have this error returned

james@bunbury:~$ smbclient //kumquat/
Password:
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

I've searched for this and I am not familiar with samba at all. The documentation I usually find for it is not as confusing as the man files. If anyone knows what to use to evade this error or to completely correct this please help me.

---

### Post by Zimmer on 2006-03-24
Have a look here for my thread regarding creating Samba users..

[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)   reply #5
and here for links to sharing issues..
[http://ubuntuforums.org/showthread.php?t=133100](http://ubuntuforums.org/showthread.php?t=133100)  reply #4

Hope this helps...

---

