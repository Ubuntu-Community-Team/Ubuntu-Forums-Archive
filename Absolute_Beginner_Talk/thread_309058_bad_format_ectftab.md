---
title: "bad format ect/ftab"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-29
I cannot start ubuntu all of a sudden. I am getting the error bad format line 15 of etc/fstab.  It cannot find swap on hda2 which is  my ubuntu partition.  I get the login screen and i try and login and I just keep getting the same login screen.

Please help how can I fix this and get my computer working.

---

### Post by rlozano on 2006-11-29
> **gentlemanmasher said:**
> I cannot start ubuntu all of a sudden. I am getting the error bad format line 15 of etc/fstab.  It cannot find swap on hda2 which is  my ubuntu partition.  I get the login screen and i try and login and I just keep getting the same login screen.

Please help how can I fix this and get my computer working.

please login in text mode, and please post your fstab content here so we can help you better. fstab file is in /etc/fstab

---

### Post by gentlemanmasher on 2006-11-29
I seemed to have fixed the fstab error now I am getting a can't find swap error.  So I did this

swapoff -a
mkswap /dev/hda5
swapon -a

Then entered the uuid from mkswap into my fstab 
still when I start i get the logon screen and try to login and I keep getting put back to the nvidia splash.  I will post fstab in a  bit

---

