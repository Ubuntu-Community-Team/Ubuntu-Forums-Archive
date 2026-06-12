---
title: "Excluding a folder from cp -ax"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by KingJohn on 2007-06-10
Super-fast question.  I am copying my entire filesystem to a new drive in preparation to switch over to a software RAID.  The new RAID (and the original drive) has 3 paritions:  /, /boot, and /home.

The new RAID is currently mounted at /mnt/md0, /mnt/md1, and /mnt/md2

*cp -axu /home /mnt/md2*  works just fine.
*cp -axu /boot /mnt/md0* works just fine.

I want to copy everything from /, without copying /boot or /home (and probably not /dev or /proc, too), to /mnt/md1.

What's the best way to do this?

---

### Post by Bohlio on 2007-06-10
cant you just go in nautilus and select everything except what you dont want and then copy if over?

---

### Post by KingJohn on 2007-06-10
...  you know, it NEVER OCCURED to me to just use the GUI.

Seriously.

I think I've been using the command line too long.

Now, this is a server machine, and so it isn't running X and doesn't have Nautilus, but I can share the two folders with Samba for a short time and use an external GUI to get my drag and drop on.

Thanks.

---

### Post by Bohlio on 2007-06-10
Lol, sometimes the GUI is the only way noobs like me know how to get things done :-P

---

### Post by KingJohn on 2007-06-10
I actually decided that just going through and manually doing each folder in turn (/bin, /etc, /var, /yadda /yadda /yadda) was faster than samba, and it was, but I really was just looking for a quick fix, and Nautilus was a smart one.

---

