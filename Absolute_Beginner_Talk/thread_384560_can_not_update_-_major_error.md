---
title: "can not update - major error"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by ldbooth on 2007-03-14
A month ago my Laptop crashed and rebooted with several partition errors. It made me erase a bunch of unknown stuff in safe mode (command line). Now I can update with the default update manager. I can check for all the new updates and download them, but can not install them. Here is the error I get the error in the following screenshot.

I am guessing a fresh install is easiest for me unless someone knows how to fix this.

---

### Post by moffa on 2007-03-14
Try running ```
 sudo dpkg --configure -a 
``` or ```
 sudo apt-get install -f 
```  They both recover interrupted updates.

---

### Post by slymi2005 on 2008-03-08
I tried both and I get the following error

dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 12 package `kdepasswd-kde4':
 EOF during value of field `Description' (missing final newline)

My computer got turned off during an update and now it won't let me update.

---

