---
title: "problem reconfiguring xserver-xorg"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Nelis on 2008-02-13
I'm having trouble reconfiguring the xserver. When I run:
```
sudo dpkg-reconfigure xserver-xorg
```

this is what happens:
```
xserver-xorg postinst warning: overwriting possibly-customized configuration file; 
backup in /etc/x11/xorg.conf.20080213210111
```

above happens when I try to setup the screen colour dept
I can't start the GUI anymore because the video driver is't working well

My video card is a VIA UniChrome CLE266 (I think)

Please help me!!!

greetings from an Ubuntu newbie

---

### Post by OffAxis on 2008-02-13
ignore it; it's just letting you know that it's creating a backup of the original file.

if you run 
```
ls /etc/X11/
```

you'll see that there's an xorg.conf file and a xorg.conf.20080213210111 file. That number is a just a date/time stamp; year/month/day/time.

If it's ever necessary you can overwrite the xorg.conf file with the backup
```
sudo mv xorg.conf.20080213210111 xorg.conf
```

and then restart the x-server
```
sudo startx
```

Instead of doing the overwrite you can just rerun the dpkg-reconfigure utility again.

I slightly easier way of doing the reconfigure is 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

which will just redo those attributes flagged as high priority; monitor and video driver.

---

### Post by Nelis on 2008-02-14
still the same :( even after I ran:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

the problem is that I can't really ignore it because the "xserver reconfigure program" just stops working

:(

---

### Post by Rocket2DMn on 2008-02-14
It's not giving you an error, just a warning, which means it should be proceeding to overwrite the xorg.conf file that was there.  It doesn't say anything about aborting does it?  With -phigh, I'm not sure you even have to answer any questions, it's more of an autoconfiguration.

---

### Post by Nelis on 2008-02-14
I got it working again!!

thanks for your help :)

---

