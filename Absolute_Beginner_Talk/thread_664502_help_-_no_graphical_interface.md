---
title: "help - no graphical interface"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by kakugan on 2008-01-11
Installed 7.10 without problems on a new phenom system.    It boots to the command line interface and I'm wondering how to get a graphical interface started.  Looking through the forums, I see the suggestion to try 
sudo apt-get install ubuntu-desktop.

this asked me for the 

[sudu] passwrod for mark

and then informs me that "mark is not in the sudoers file"

but it's a fresh install with only one user.

I'm totally out of my league here, not having used much command line interface since the 80's when I was pretty good at DOS.

thanks everyone.

Mark

---

### Post by tchoklat on 2008-01-11
odd that it boots to a command line. Try the command startx This should involke the X windows manager.
 
tchoklat

---

### Post by LeAstrale on 2008-01-11
i have had this problem once, it was caused by an error in the alternate installer cd, when you have choosen somethings and then go back to alter other settings the user settings simetimes dissapear. The easiest solution for me at the time was to just reinstall while watching the movie i had just started. and after that it worked.

---

### Post by geirha on 2008-01-11
In short: This shouldn't happen. 

Something must have gone wrong during the install, but what that might be, I have no idea. Could you boot the CD, and at the boot menu, choose Check CD for defects (or something along those lines) to check that the CD is OK?

If it detects errors, try burning the CD again, at a low burning speed. 

If it does not detect errors, boot the CD and paste the output of ```
sudo fdisk -l
``` and also, mount the partitions (Open nautilus by clicking Places -> Desktop, then on the left-hand-side of the window that pops up, it should list all partitions, double-click them to mount them), and paste the output of /etc/sudoers on the / partition. You can do this by opening a terminal (Applications -> Accessories -> Terminal) and type this in the terminal ```
sudo cat /media/disk/etc/sudoers
``` If the above command produces an error, it's probably the wrong partition, so just try all partitions untill you find the correct one, i.e. ```
sudo cat /media/disk1/etc/sudoers
sudo cat /media/disk2/etc/sudoers
```

And lastly, since you haven't used your system yet, trying to install ubuntu again might be worth a try, to see if you get the same result.

---

