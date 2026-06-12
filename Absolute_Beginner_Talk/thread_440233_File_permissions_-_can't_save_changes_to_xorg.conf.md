---
title: "File permissions - can't save changes to xorg.conf!"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by overandunder on 2007-05-11
Hi

Just installed Feisty and all ok but need to alter my video settings.  I have found the help page for this but after editing xorg.conf and trying to save it the system says that the file is owned by root and I (as a user) can view it but not save any changes.  

I guess I need to login as root - but how do I do this please?  If I try from the 'switch user' screen it doesn't work.  Have tried sudo -i as well and that didn't work!  Have tried looking through the documentation pages but that explains the principles of root usage rather than come up with some useful commands. HELP!!!

---

### Post by aysiu on 2007-05-11
This will help you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Aberrix on 2007-05-11
> **overandunder said:**
> 

I guess I need to login as root - but how do I do this please? 

from the command line, type 'sudo su -' you will then be root, then just do a 'vi /path/filename' and save it. or just do a 'sudo vi /path/filename' from the command line as well.

---

### Post by kvonb on 2007-05-11
Press <alt><f2> and type : gksu gedit /etc/X11/xorg.conf into it (just copy and paste that).

We don't encourage logging in as root, that might seem a bit heavy handed, but there is a good reason for it, and there is a very simple way around it.

Whenever you enter a terminal command that needs root privileges, simply precede it with sudo.

---

### Post by overandunder on 2007-05-11
Thanks to all for the quick response.  I have 3 home PC's to convert from Windoze XP and this the first machine so am making sure everything is a -ok.  Very impressed so far.

---

