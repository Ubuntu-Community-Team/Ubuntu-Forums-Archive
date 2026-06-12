---
title: "Need help restoring file"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by c1700 on 2007-05-11
I got Ubuntu working great last night with Beryl but when I tried to set up my dual monitors I messed up the xorg config file and no I can't even boot. I copied my old file to my desktop before I started messing with it but now I can't figure out how to copy it back.  I tried using the live cd but I don't have permissions. I also deleted all the safe startup options from GRUB before this so I can't get in that way. Can anyone help? Thanks.

---

### Post by vikram on 2007-05-11
using the live CD, open the terminal and mount your local hard drive to get access to it.

try 

sudo mkdir /myhd

sudo mount /dev/hda1 /myhd

now you can access your harddisk with the HD root drive as /myhd and copy the file.

hope this works.

---

### Post by c1700 on 2007-05-11
Thanks. I will try that. I was able to mount the partition in the GUI but did not have write access.

---

