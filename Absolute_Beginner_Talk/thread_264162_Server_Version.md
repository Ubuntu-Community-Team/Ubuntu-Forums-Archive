---
title: "Server Version"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by lcarsdata on 2006-09-24
So, today I installed the alternative version by accident. After installing I realised that I clicked on the wrong link and downloaded that instead of the server version I wanted.

I install the server edition, but it was not what I expected, no GUI. Is there a way I can add a GUI to it because I wanted the mysql and php capabilities of it. If there isn't could someone tell me how to use the command version or give me a link to a guide.

Thanks

---

### Post by dbd on 2006-09-24
I think the command:
sudo apt-get install ubuntu-desktop
will install everything you need. Then just use the command startx to get it going (or rebooting will probably work too)

---

### Post by henriquemaia on 2006-09-24
Taken from this post:

[http://ubuntuforums.org/showpost.php?p=1521156&postcount=7](http://ubuntuforums.org/showpost.php?p=1521156&postcount=7)

> **kerry_s said:**
> server install
login >sudo su < to become root
nano /etc/apt/sources.list
comment(#) out the cdrom and uncomment all the repo's
apt-get update
apt-get install x-window-system-core xterm synaptic 
apt-get install gdm fluxbox(or icewm, wmaker, gnome-core, kdebase...)
reboot
select your wm in session and login


This will do a minimal desktop install (as opposite to the sugestion of the previous poster).

---

### Post by lcarsdata on 2006-09-24
I really wanted the whole thing so I tried the first option but I just get a message syaing that it couldn't find the package ubuntu-desktop.

---

### Post by lcarsdata on 2006-09-24
Do you need to be connected to the internet to do this?

---

### Post by furiousV on 2006-09-24
> **lcarsdata said:**
> Do you need to be connected to the internet to do this?

Yes, you do. the **apt-get** commands are getting all the information and packages off the Ubuntu repositories.

---

### Post by az on 2006-09-24
> **furiousV said:**
> Yes, you do. the **apt-get** commands are getting all the information and packages off the Ubuntu repositories.

No, if the person is not online to begin with, the Ubuntu install does not know about the online repos.

You probably downloaded the server version and not the alternate version.  The server version does not install a GUI.

---

