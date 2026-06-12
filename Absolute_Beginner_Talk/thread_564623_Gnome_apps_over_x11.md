---
title: "Gnome apps over x11"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by ne0trace on 2007-10-01
Hello,
I am currently working over SSH with my Ubuntu 7.04 machine. I currently have no display to connect which is normally no problem as I am using SSH as I said. But sometimes I need to use a tool which is only accessible through Gnome.

as here:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

To configure Myth, you run the mythtv-setup utility and step through the options. Select it from the menu: System->Administration->MythTV Backend Setup

This is something that I cannot do over SSH?
I did not manage to get VNC or RDC running, but I remember that X11 can run gnome apps.

My post is a bit confusing but I hope that somebody will understand what I am thinking of. :popcorn:

ne0trace

---

### Post by mvs1207 on 2007-10-01
edit your /etc/ssh/ssh_config 

ForwardX11 yes
ForwardX11Trusted yes

---

### Post by ne0trace on 2007-10-01
That is already working. But what command starts System->Administration->MythTV Backend Setup ???

---

### Post by ne0trace on 2007-10-02
Bömp

---

### Post by ruibernardo on 2007-10-02
Right-click on the menu and search for that shortcut in Administration. Double click the shortcut to see what command it calls.

---

### Post by ne0trace on 2007-10-03
Cool that seemed to work...

---

