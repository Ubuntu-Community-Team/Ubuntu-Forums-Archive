---
title: "ubuntu studio problem"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by LE CHARBON on 2007-05-11
I installed it. but when it loads is goes black then a blue white screen and says something about toe not configured in a weird kind of way.  any ideas:confused:

---

### Post by Billy McCann on 2007-05-12
Probably Xserver.  

Does it drop you to a command line?    

If so, run 

```
dpkg-reconfigure xserver-xorg
```

You may need to place a 'sudo' before that command.  If you reboot into recovery mode, you'll be able to do this as well.    

Stubuntu probably just didn't select the correct video driver.  If you don't know which driver to use, select the VESA driver.  Don't be tempted to startx at this point (you may do something dumb like connect to freenode as root or something).  Just reboot once you've reconfigured the xserver.    

What video card do you have?  Maybe we can point you in the right direction.

---

### Post by LE CHARBON on 2007-05-12
i have a internal intel 82865g grapgics controller 1280x1024 resolution at 60-75hz. this is on a dell e770 flatscreen plug and play. i did what you said and it did not help. I erased it and will try again fresh. Any ideas on what I should look for? Especially when it asks about resolution?

---

### Post by happy-and-lost on 2007-05-12
On mine it defaulted to the vesa driver in xorg.conf, just change that to the name of the driver you use in nano(/vi/whatever CLI text editor you like!) and it should work a charm

---

### Post by human on 2007-05-12
In case you don't happen to know what driver that might be, It is most likely the i810 driver (at least it is for me on my integrated 82845G chipset).

---

### Post by happy-and-lost on 2007-05-13
Yup, login to bash once it's finished complaining about Xorg, and...

```
sudo nano /etc/X11/xorg.conf
```

and go down to the Device seciton and replace "vesa" with "i810"

Should work a charm.

---

### Post by LE CHARBON on 2007-05-13
Thanks!!

---

