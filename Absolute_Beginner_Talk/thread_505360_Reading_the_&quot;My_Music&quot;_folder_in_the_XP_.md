---
title: "Reading the &quot;My Music&quot; folder in the XP partition from Ubuntu?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by jimbojames on 2007-07-20
Hi All,

[SIZE="5"]WARNING - COMPLETE NUBE ALERT!!!!![/SIZE]

I only started looking at Ubuntu 2 days ago and in that time I already installed it on my PC with no real issues apart from a bit of an upset with my Belkin wireless USB dongle (which I have a work round for .... a  router!) and my ATI X600 graphics card isn't being loved by Ubuntu at the moment but even so I LOVE UBUNTU :), I wish i could kill XP all together but I still need it for some stuff.

Anyway - I have been looking around but don't seen to have found a solution for my next query.  I have about 30GB of music in my "My Music" folder on my C drive (NTFS) so would like to find a way of getting Ubuntu to read the "My Music" folder in the XP partition, is it possible?  I had found a thread but it was from 2005 saying that NTFS read and write is still not fully mature - is this still the case?

Thanks in advance, 

James

---

### Post by eentonig on 2007-07-20
search for "ntfs-3g" and install that via Synaptic.

You'll get a GUI to enable it under System\Administration where you can enable R/RW support for your ntfs partitions. It works very well (I never had any problems). The only thing you need to take in account, is that you will need to properly shut down windows (no hibernate, no unclean shutting down) when you want to use it.

---

### Post by civilmonkey on 2007-07-20
Welcome!

There is a lot of great information if you use the search command.  For instance, I quickly found this link which should help you

[http://ubuntuforums.org/showthread.php?t=504354&highlight=read+xp+partitions+mount]("http://ubuntuforums.org/showthread.php?t=504354&highlight=read+xp+partitions+mount")

You'll need to mount the windows harddisk so you can read from it.  If you want you can make a directory (folder):

```
mkdir /media/mymusic
```

and mount the windows music folder to the new directory you just made so you'll have easy access to it.

FYI: Ubuntu can read windows NTFS partitions but not write them them unless you install additional software.

Good luck!

---

### Post by Mornedhel on 2007-07-20
NTFS reading is mature. NTFS writing is still experimental, but works. If you cannot read your NTFS drive as a normal user, edit your /etc/fstab file to change its umask to 000 (warning : backup your fstab before you do anything, read the fstab man page to understand what you are doing) and reboot.

---

### Post by jimbojames on 2007-07-20
Thank you all for your help and advice, I'll give it a go when I get home.

Thanks again,

James :)

---

