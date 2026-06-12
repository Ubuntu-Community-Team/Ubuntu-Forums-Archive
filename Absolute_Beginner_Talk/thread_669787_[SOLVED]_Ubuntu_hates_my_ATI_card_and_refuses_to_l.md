---
title: "[SOLVED] Ubuntu hates my ATI card and refuses to look at my drivers."
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-16
Right now I seem to have no idea what I'm doing to get the drivers for my ATI 9600 Pro installed.

First I tried **System // Admin // Restricted Drivers Manager** and enabling the "ATI accelerated graphics driver"; but that just spits out an error:

"xorg-driver-fglrx is not enabled".

I tried the recommendations found [here ]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")as well, but that hasn't done anything.

I even downloaded the drivers from ATI's website (something in a .RUN format) but it keeps telling me I need to run it as a superuser, and I haven't a clue what command I need to use in conjunction with **sudo **to do that.

I was wondering if anyone had any thoughts on this because I haven't a clue what I'm doing.

---

### Post by Joeb454 on 2008-01-16
Lets say the file is called **ATi.run** and is in your home folder.

Open a Terminal and type

```
 sudo /home/your_username_/ATi.run 
```

Just remember to replace the /home part with the correct path

---

### Post by toastysquirrel on 2008-01-17
Thanks JoeB454, apparently I was neglecting to include the full path along with the file name.  Now for my next incredibly newb question:

How do I configure the driver, or ensure that the correct driver is being used.  XP had the Device Manager or the Display Settings.  I tried futzing around with Settings // Admin // Screens and Graphics, but I'm not sure it did anything.  As a test I tried changing my screensaver to some of the fancy (installed by default) screen savers and when I selected "Antinpect" it kicked me out and returned me to the login screen. :confused:

---

