---
title: "[SOLVED] Installing Printer Driver"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by loren41 on 2008-04-13
I downloaded a linux printer driver (hplip-2.8.4.run) to my desktop, but don't know how to install it from there.  The distro says I should type sh filename, but the program can't find the file.  How should I proceed?

---

### Post by sisco311 on 2008-04-13
open a terminal:

Applications -> Accessories -> Terminal

change the directory to Desktop
```
cd Desktop
```make the file executable
```
chmod a+x ./hplip-2.8.4.run
```run the file
```
sudo sh ./hplip-2.8.4.run
```

---

### Post by Moop on 2008-04-13
You may not need that driver. Have you tried adding your printer through System-Administration-Printing?  I have a HP printer and didn't need to download a driver. 

Before you can run that command you need to change to the directory it was downloaded to. ```
cd Desktop
```

---

### Post by loren41 on 2008-04-13
Thanks guys, that should help.

---

### Post by Sef on 2008-04-13
What HP printer do you have?

---

### Post by OzFitzy on 2008-04-28
As an absolute beginner (with Ubuntu 8.04 or earlier) I find a network connection is essential in overcoming dependency problems when installing (hplip-2.8.4.run) but I (and also another guy doing the same install with 7.01) both keep getting the following error:-

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes python2.5-dev'
Please wait, this may take several minutes...
[COLOR="Red"]error: Package install command failed with error code 100[/COLOR]
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 


Any clues welcome :)

---

