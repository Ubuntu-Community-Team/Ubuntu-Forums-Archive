---
title: "Drivers..or something ?"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by pinkpanther01010 on 2006-02-23
Alright, I had a kernel my friend compiled for me and it was working fine for like 2 weeks +.

And I got this problem when I took my tv-tuner card out of my computer (for selling.)

But I got the whole Xorg not working kind of errors..so I try downloading the drivers and what not, no luck.

So I manually go into the /etc/X11/xorg.conf and was going to post it on the forums and ask if you guys can see what's up.

But now I changed where it said the driver "nvidia" to "nv" and rebooted, now instead of getting a terminal type screen, I get this little box floating around my screen saying Hz   ?.    

I have no idea what to do now and can't even edit anything..I have a server setup in my home so I could most likely SSH into it (with some help) and edit it back.

But until then..please help !  I should be checking this forum about every 10 minutes, it's my fav computer :(.

---

### Post by joshuapurcell on 2006-02-23
While that box is floating around saying "Hz" something or other, hit Alt-Ctrl-F1 to get to a terminal window. Log in, then you can edit the xorg.conf file to whatever it was before. After that, restart the gdm service:```
sudo /etc/init.d/gdm restart
```This should automatically try to start X (taking you to the terminal located at F7). What you need to do is press Ctrl-Alt-F1 again to go back to the terminal window you were at. Now you should see some information printed out from running the gdm restart command (and possibly errors that will tell you what needs to be fixed). Post what you find there.

If you have any questions then post them here.

---

### Post by pinkpanther01010 on 2006-02-24
Alright, when I did that, it went to a gray/black screen and flashed 3 times. 

It does that same thing when it's first starting up so it looks/sounds like it's unable to load the drivers ?

And now that it did that I can't hit ctl+alt+f1 or f7 :(.

---

### Post by joshuapurcell on 2006-02-24
You could boot up into rescue-mode (by selecting the alternate kernel option in the GRUB menu during startup) and view the xorg logs at that time. The logs are located at /var/log/Xorg.log. See if you find any errors (lines with EE close to the beginning) in those files and post them here. A quick way to get the errors out of this file is by running this command:```
more /var/log/Xorg.log | grep EE
```

---

### Post by pinkpanther01010 on 2006-02-24
When I try to do that, it says --

/var/log/Xorg.log: No such file or directory

---

### Post by joshuapurcell on 2006-02-24
[QUOTE=pinkpanther01010]When I try to do that, it says --

/var/log/Xorg.log: No such file or directory[/QUOTE]Move to the needed directory:```
cd /var/log
```Then list all the files starting with Xorg in order of last accessed:```
ls -halt Xorg*
```Take a look at these files using the more command given earlier and see what errors you can find.

---

### Post by pinkpanther01010 on 2006-02-25
When i ls-halt Xorg*, it says the last ones used were

Xorg.0.log
Xorg0.log.old
Xorg.20.log

Now the computer was running fine actually yesterday but my friends hit the restart button and now I have the same drivers problem..so I really don't know what's going on.

Also when it WAS working, when I would try to open programs it would give me an error saying "Segmentation fault" ?

---

