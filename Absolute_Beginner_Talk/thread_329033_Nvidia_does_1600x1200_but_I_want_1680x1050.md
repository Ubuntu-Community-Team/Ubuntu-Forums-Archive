---
title: "Nvidia does 1600x1200 but I want 1680x1050"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by lowracer on 2006-12-31
Can anyone explain, why when I power off my machine, leave town for a week, then when I come home and power back up, instead of running in 1680x1050 mode, which it has done for the last several months without fail even after resetting power or rebooting, it is now stuck in a 1600x1200 virtual mode (where you can't see all the pixels unless you move your mouse off screen).  I do not want this mode, yet here it is.  

I look at my xorg.conf file, and it used to make sense, I spent a lot of time figuring it out when I first started learning Ubuntu linux, now I don't even recognize it.  modeline is the new line I don't recognize and there isn't one for the 1680x1050 resolution, which is the max resolution on my Samsung 205bw 20" widescreen.

What happened?  How do I get back to 1680x1050? 

Thanks!
-mark

---

### Post by handy on 2006-12-31
Hi, I would try deleting all 1600x1200 references in your xorg.conf & replacing them with the 1680x1050 res' that you desire.

I don't know what has changed your xorg.conf?

The other thing you could do, it just occured to me, is have a look in /etc/X11/ you may find that when your xorg.conf was modified that a backup was created, so check out the dates on any backup files & look into them.

Best I can do for you... 

Happy new year... :KS

---

### Post by lowracer on 2006-12-31
Checking the directory did the trick.  I found an xorg.conf.1 file dated 12-24 of this year.  I must have updated something that laid down a new xorg.conf file.  The xorg.conf.1 file was the type I recognized without all the modelines.  Copying the .1 file over the xorg.conf file and restarting X has solved the problem!

Thanks!
-mark

---

### Post by handy on 2006-12-31
It's cool  :cool:  how many of these important files get automatically backed up after they are modified. :)

---

