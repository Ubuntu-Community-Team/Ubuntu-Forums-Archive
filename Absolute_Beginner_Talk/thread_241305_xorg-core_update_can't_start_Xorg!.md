---
title: "xorg-core update can't start Xorg!"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-22
Hi, I recently added some extra repositories and without thinking did an update of xorg-core and after rebooting, it fails to start xorg and thus I can't get into the GUI, I do have access to the command line is there a command I can put in there to force it back to the previous version it was using? (I was using the one everyone would be using! but I don't know the version number!)

Reconfiguring xorg using sudo dpkg-reconfigure xsrver-xorg (not sure thats exactly right but I did use the right one!) doesn't fix the problem.

Please Help!

Calv

---

### Post by FrzzMan on 2006-08-22
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

---

### Post by MaximB on 2006-08-22
[http://www.ubuntuforums.org/showthread.php?p=1408007#post1408007](http://www.ubuntuforums.org/showthread.php?p=1408007#post1408007)

---

### Post by calvinthomas on 2006-08-22
Thankyou, had to change to vesa driver then reinstall my ati driver but that went without a hitch! Thanks for the help!

Calv

---

### Post by ubuntu_demon on 2006-08-22
I've closed this thread. 

Let's keep this discussion in one place :
[B]
PLEASE READ: The Latest Updates Break the Xserver!
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)[/B]

---

