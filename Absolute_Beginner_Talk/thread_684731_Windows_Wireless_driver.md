---
title: "Windows Wireless driver"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by polomaan on 2008-02-01
I managed to get everything working fine wirelessly with a windows driver using the "windows wireless drivers" utility in Gusty.  The problem is that my comp doesn't recognize the driver after I restart Ubuntu.  So I have to uninstall the driver and reinstall it every time I restart.  It doesn't take much time but it's annoying.  Could it be the place where I put the wireless driver?...it's in a folder in my "documents" folder....since I didn't know where else to put it.  Thanks for the help!

---

### Post by alan34 on 2008-02-01
You could try editing your /etc/modules file which loads drivers to the kernel when the computer
is booting.

Go Applications - Accessories - terminal

Then

sudo cp /etc/modules /etc/modules.backup

this backs up the original file, then

sudo gedit /etc/modules

and add

ndiswrapper at the end on a line by itself should look like this

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper



 then save and exit and restart.

To restore your original file either edit it again or

sudo cp /etc/modules.backup /etc/modules

Good luck

---

### Post by polomaan on 2008-02-02
worked perfectly.  Thanks!!

---

