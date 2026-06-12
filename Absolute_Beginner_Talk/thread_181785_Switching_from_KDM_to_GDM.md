---
title: "Switching from KDM to GDM"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-05-24
How do I configure GDM to be the default?
thanks

---

### Post by byen on 2006-05-24
try this command at the terminal:if you are in gnome
```
sudo dpkg-reconfigure gdm
``` if you are in Kde
```
sudo dpkg-reconfigure kdm
``` 

(actually I think any  of the two should work irrespective of which dm you are logged into)

select the desired manager and that should fix it :P

---

### Post by Caligula on 2006-05-24
thanks,
but that's what I get...

> caligula@anarchy:~$ sudo dpkg-reconfigure gdm
Password:
grep: /etc/X11/default-display-manager: No such file or directory
 * Reloading GNOME Display Manager configuration...  * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
caligula@anarchy:~$


What does that mean?

---

### Post by aysiu on 2006-05-24
I don't know, but apparently, there's a bug report on it:
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29389](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29389)

You could try this: ```
sudo nano /etc/X11/default-display-manager
``` Then in the blank document type ```
/usr/sbin/gdm
``` and save (control-x), confirm (y), and exit (Enter).

---

### Post by Caligula on 2006-05-24
yep, it wrote it automatically, i checked the file..
it's working..

thanks

---

