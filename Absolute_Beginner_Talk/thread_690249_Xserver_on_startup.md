---
title: "Xserver on startup"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by godM0d3 on 2008-02-07
This may be a ridiculous thing to ask, but I want to disable Xserver loading automatically on startup.  I've tried google several times and I can't really find anything helpful.  There aren't any problems with it, I'm just using the machine remotely and have no need for the actually box to be doing much.

---

### Post by taurus on 2008-02-07
```
sudo /etc/init.d/gdm stop
sudo apt-get remove gdm
```

---

### Post by godM0d3 on 2008-02-07
Thanks.

---

### Post by Liet_Kynes on 2008-02-07
What if you don't want to remove gdm entirely? You just don't want it starting automatically everytime?

---

### Post by alarme on 2008-02-07
Don't uninstall gdm

$ ls /etc/rc2.d | grep gdm
the result of this command must be some like:
S30gdm

then remove this link and gdm won't execute on startup
$ sudo rm /etc/rc2.d/S30gdm

Also, you can made this installing sysv-rc-conf from synaptic.  This utility allows to select what services/programs run at startup.  Ubuntu user session is rc2.  Don't play with the other columns if you don't understand how they work.

---

### Post by Liet_Kynes on 2008-02-07
Thanks. Am i right in assuming that typin gdm at a term will then start gdm when you want gui session?


Also if i ever want to replace auto gdm start how would I go about that?

---

### Post by alarme on 2008-02-07
$ sudo /etc/init.d/gdm start
Also, you can change start for stop or restart

All the services can be started or stopped if you call them on /etc/init.d followed with the action (start, stop, or restart)

For example, if you modify the smb.conf file (for shared files with samba), the changes you made take effect when you restart the samba daemon writing   $ sudo /etc/init.d/samba restart

---

### Post by alarme on 2008-02-07
If you plan to start automatically gdm in other time, don't remove the link.  Cancel the x permission:

assuming the result of 
$ sudo ls /etc/rc2.d | grep gdm
is
S30gdm

Disable gdm at startup:
$ sudo chmod -x /etc/rc2.d/S30gdm

Enable gdm at startup:
$ sudo chmod +x /etc/rc2.d/S30gdm

Or more easy, install sysv-rc-conf, and mark the service as active another time.

---

