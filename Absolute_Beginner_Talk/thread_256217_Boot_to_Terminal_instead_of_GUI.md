---
title: "Boot to Terminal instead of GUI"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by ChunkyBustout on 2006-09-12
Hello,

How do I boot up to a terminal as opposed to the gui? If I can do this permanently and start GDM manually would be ideal.

Please don't assume I know anything about Linux. I'm a complete Linux Noobie!

Thank you.

---

### Post by shoot2kill on 2006-09-12
i dont know, but when u have booted to GUI, u can press

CTRL + ALT + F1 

to go to full terminal

---

### Post by SeanHodges on 2006-09-12
load up a terminal and type:

```
sudo cp /etc/X11/default-display-manager /etc/X11/default-display-manager-backup

sudo gedit /etc/X11/default-display-manager
```

The file that loads should contain "/usr/bin/gdm". Remove this text and save the file. This will force the boot process to not load any display manager (like GDM or KDM).

Once you reboot, you should be in the command line. Login and away you go. to start GNOME you can type "startx" at any time.

The default file is backed up as "default-display-manager-backup", so copy it back if you ever want to go back to the original configuration (with GDM).

---

### Post by mitch.c on 2006-09-12
You need to remove gdm from the default runlevel. I use bum (boot up manager) to change init scripts:
```
sudo apt-get install bum
```
But really, it's easier to change to a virtual terminal as suggested previously.
```
<Alt><Ctrl><F1> ... <F6>
```
To switch back to GUI terminal
```
<Alt><Ctrl><F7>
```
Best of both worlds! And a lot easier especially if you really a newb. :roll:

---

### Post by steve.horsley on 2006-09-12
Another thread discussing this:
[http://www.ubuntuforums.org/showthread.php?t=256030](http://www.ubuntuforums.org/showthread.php?t=256030)

---

### Post by SeanHodges on 2006-09-13
At least for me, and most others I know; the <Ctrl> <Alt> <F1> etc method doesnt work while your at the login screen (GDM)... You need to select "Console Login" in the Options. 

The key combination should work fine when you're logged into a session though.

Setting the runlevel will do have the same outcome as the default-display-manager method... But perhaps changing runlevels is the proper way to do it, i dont know.

A few options to consider tho ;)


You also asked how to start GDM manually from the console... You need to type:

```
sudo gdm
```

at the command prompt, and type your password.

---

### Post by 1oki on 2006-09-21
hmm... cntl alt f1 doesnt work for me at all... lol it used to, but idk what happened to it... bla any sugestions as to how to get kill xserver?

---

### Post by azidrane on 2006-10-11
> **mitch.c said:**
> You need to remove gdm from the default runlevel. I use bum (boot up manager) to change init scripts:


Thanks for this chap! This is the type of util i've been looking for!

Cheers!

---

