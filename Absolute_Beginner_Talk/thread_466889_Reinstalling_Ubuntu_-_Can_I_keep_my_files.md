---
title: "Reinstalling Ubuntu - Can I keep my files?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by InternationalRescue on 2007-06-07
Hi, due to a graphics problem, i can no longer access my ubuntu account when i try to login. After I login, a white screen appears and it doesnt go, so my desktop is inaccessible. I am planning on reinstalling ubuntu feisty (it was working fine until i fiddled around with some graphics option) and i was wondering if it possible to keep all my files, as i have several GBs of family pictures i dont want to lose. i know there are options to partition the hard drive when i install ubuntu, but is this the right option? any help would be appreciated, thanks!

---

### Post by gerscht on 2007-06-07
Can you post the output of /etc/fstab?
```
sudo les /etc/fstab
```
It might be the case that you have your /home on a different partition already, then it's not a problem to keep the files.
If not, you might want to copy them somewhere save first, and create a dedicated /home partition during installation

---

### Post by jverkamp on 2007-06-07
You have at least a couple of options:
 - Use a LiveCD to back the files up to an external hard drive or another partition.
 - Boot into recovery mode (if that's an option in GRUB) and use the console to do the same.
 - With the install partitioner, shrink your current partitions and install on a new one. (You'll have two copies of the system but you will have your data.)

Personally, the LiveCD or recovery mode would probably be best.  Actually, if you could figure out what broke, you might be able to access the configuration files on the original partition and undo it.

---

### Post by locke.dragon on 2007-06-07
yeah.  i've had many a time when i screwed with some setting and borked my system.  i just pop the live cd in, mount my drive, and fix whatever went wrong!  :D  if all else fails, just put all your pictures on a cd through the live cd and you'll be all set.

---

### Post by eshen on 2007-06-07
> **gerscht said:**
> ...create a dedicated /home partition during installation
How would I go about doing this?

---

### Post by locke.dragon on 2007-06-07
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

it's easier to do it after you already have an ubuntu installation running.

---

