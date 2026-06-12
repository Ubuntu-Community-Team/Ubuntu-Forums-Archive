---
title: "iBook G3 display issue - screen repeats on left &amp; black bar on right side"
date: 2009-02-12
forum: Apple Hardware Users
---

### Post by guthrie on 2009-02-12
I have an iBook that shrinks the desktop and repeats it down the left hand side of the display, With a black bar along the right side that I assume is just "unused space" also between the 2 repeating desktop screens there is a grey bar that runs horizontally across the monitor, including the "unused space. I'm not too familiar with the command line so I wanted to try to get some situation specific answers first before I go trying random things. Thanks in advance. 

I hope that this explanation makes sense.

---

### Post by ghostz on 2009-02-21
i have the same damn problem but cannot find any solution but modifying the xorg.conf file that u cannot gain permission for so if u have fixed this let me know i want mine to work

---

### Post by cyberdork33 on 2009-02-21
> **ghostz said:**
> i have the same damn problem but cannot find any solution but modifying the xorg.conf file that u cannot gain permission for so if u have fixed this let me know i want mine to work
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by ghostz on 2009-02-21
> **cyberdork33 said:**
> ```
sudo nano /etc/X11/xorg.conf
```

i have tried that but no go lol its kinda impossible to get permission to i even logged in to root user to try it and no go

---

### Post by cyberdork33 on 2009-02-21
> **ghostz said:**
> i have tried that but no go lol its kinda impossible to get permission to i even logged in to root user to try it and no go
that doesn't make any sense at all. what is the error you are getting?

---

### Post by ghostz on 2009-02-21
> **cyberdork33 said:**
> that doesn't make any sense at all. what is the error you are getting?

sorry um i get an error when i try to open the xorg.cof it opens a blank page when i type this:```
sudo gedit or nano /etc/x11/xorg.conf
``` i even tried```
sudo -i
``` to login to root user ai tried to edit it and it would give me the same error and i dont know what else to do

---

### Post by cyberdork33 on 2009-02-22
> **ghostz said:**
> sorry um i get an error when i try to open the xorg.cof it opens a blank page when i type this:```
sudo gedit or nano /etc/x11/xorg.conf
``` i even tried```
sudo -i
``` to login to root user ai tried to edit it and it would give me the same error and i dont know what else to do
ok, what is the error? can you type it exactly.

---

### Post by bronzehedwick on 2009-04-13
> **cyberdork33 said:**
> ok, what is the error? can you type it exactly.

I have the same problem on my iBook G3. The error I get is
```
username is not in the sudoers file. This incident will be reported.
```
Any thoughts?

---

### Post by cyberdork33 on 2009-04-13
> **bronzehedwick said:**
> I have the same problem on my iBook G3. The error I get is
```
username is not in the sudoers file. This incident will be reported.
```Any thoughts?
[http://ubuntuforums.org/showthread.php?t=1118382](http://ubuntuforums.org/showthread.php?t=1118382)

---

### Post by stream303 on 2009-04-13
Watch out for the capital X in X11

/etc/X11/xorg.conf

This can also creep up on you when looking at the logfile for X

/var/log/Xorg.0.log

:)

---

### Post by cyberdork33 on 2009-04-14
> **stream303 said:**
> Watch out for the capital X in X11

/etc/X11/xorg.conf

This can also creep up on you when looking at the logfile for X

/var/log/Xorg.0.log

:)
yep. Tab-Completion is your friend

---

