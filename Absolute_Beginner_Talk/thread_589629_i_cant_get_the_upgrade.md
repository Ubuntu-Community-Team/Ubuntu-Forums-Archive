---
title: "i cant get the upgrade"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by crazysexycool on 2007-10-24
hello i go to update manager and it doesnt find the upgrade i dont want to a clean install any ideas:(

---

### Post by Qwerty_ on 2007-10-24
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by crazysexycool on 2007-10-24
Thanks but i dont want to do a clean install

---

### Post by Seisen on 2007-10-24
Try```
 gksudo update-manager -c 
``` in the terminal.

---

### Post by crazysexycool on 2007-10-24
here is the error i get


cheeseboi@cheeseboi-laptop:~$ sudo update-manager -c
Password:
warning: could not initiate dbus
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
cheeseboi@cheeseboi-laptop:~$

---

