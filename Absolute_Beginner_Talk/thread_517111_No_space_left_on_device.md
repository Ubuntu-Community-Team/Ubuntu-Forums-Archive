---
title: "No space left on device"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by BrokenBelief on 2007-08-04
Well, of course, when I'm just trying to learn how to operate this OS, I get the unexplainable error.  Apparently I have "No space left on device."  I checked the partitions and such, and it all seems to be in order.  After searching the net for a little while, I tried the df -i command.  My results are as follows.

```
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
tmpfs                 129258      17  129241    1% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 129258      17  129241    1% /lib/modules/2.6.20-15-generic/volatile
varrun                129258      54  129204    1% /var/run
varlock               129258       2  129256    1% /var/lock
udev                  129258    2989  126269    3% /dev
devshm                129258       1  129257    1% /dev/shm
tmpfs                 129258      87  129171    1% /tmp
/dev/sda2             120448  120336     112  100% /media/disk
/dev/sda1                  0       0       0    -  /media/DellUtility
/dev/sda3                  0       0       0    -  /media/DellRestore

```

It seems I am out of Inodes on /dev/sda2,  The problem is, I have no idea what this means and how to fix it.  Any help would be appreciated, and remember, I'm a total noob, so try and dumb it down as best as possible.

---

### Post by lisati on 2007-08-04
A quick question: are you using a PC made by Dell? It could be something to do with how Dell set up your system, e.g. recovery partitions.

---

### Post by southernman on 2007-08-04
what does "df -h" show you?

---

### Post by radioraheem8 on 2007-08-23
I am getting the same message, but what's weird is that I have an assload of space (well, about 20 gigs) left.  

Is there any reason I would get that message with a nearly blank HDD?  All I have on it is the ubuntu OS, which I tried to install last night.  I got a dpkg --configure -a message when I couldn't get the update, so I ran the dpkg configure, but then I get the "No space left on device", so I check the HDD and find plenty of room left.  Am I missing something really obvious?  

One thing I did do at the beginning, was first install the Server version, but when I got the error when trying to do the update, I decided to run off the Desktop version since it had a GUI and I'm completely new to this type of system.  Could that be causing a conflict of sorts?  Should I just format my HDD and reinstall desktop version?  

Thanks!

---

### Post by rexy on 2007-08-23
post your df -h output and the exact error you get and when?

---

### Post by radioraheem8 on 2007-08-23
Ah, crap.  I probably should have posted this from my home cpu instead.  I'm stuck at work now, but I'll be sure to post everything when I get home.  Thanks.

---

