---
title: "Ubuntu server - disk space not freeing up"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by earlaker on 2007-06-05
I am running Ubuntu server 7.04 on an IBM X series server. My df output is as follows:

root@pvscdnstz04:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            135348936 128853588         0 100% /
varrun                 1037924        72   1037852   1% /var/run
varlock                1037924         0   1037924   0% /var/lock
procbususb             1037924        60   1037864   1% /proc/bus/usb
udev                   1037924        60   1037864   1% /dev
devshm                 1037924         0   1037924   0% /dev/shm
root@pvscdnstz04:~#

As you can tell, the used vs available has a rather large disrepency. I have done some googling, and the only reference I can find is to look for a .trash folder, except I am not running X on this server. As well, it is running VMWare 1.0.2, so as a result, my virtual servers have decided to say "piss off, I'm not running" as it thinks there is no hard drive space left.

My first question is: What the hell? Ok, I kid. My first and only question is how the heck do I get the system to free up that drive space?

---

### Post by earlaker on 2007-06-05
I am dumb.

I did more googling after I involved a linux guy who works in our office. That led me down the ext3 path, and more specifically, the reserved space it allocates (default being 5 percent) so as to ensure the filesystem doesn't fail when it gets all filled up. I used tunefs -m 1 /dev/sda1 to reduce the reserved space to 1 percent of the filesystem total, and voila! 5+ gigs free.  All the numbers now add up.

---

