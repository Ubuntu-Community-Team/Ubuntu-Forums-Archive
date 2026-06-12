---
title: "[SOLVED] How to mount things where I want them?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Excalibre on 2007-10-27
There's a couple partitions that show up on my desktop automatically; one of them is a tiny (like, 50 megs or so) fat16 partition that Dell apparently put on my hard drive for their own inscrutable purposes. The other is my shared Linux-Windows data partition.

A) I'd like to mount that data partition somewhere other than where I chose during installation. How do I change that? I tried unmounting it, but it said that only root could do that. (I thought there wasn't a root account with Ubuntu . . . )

B) How do I get the damn things off my desktop? Gnome is putting them there and I can't find the preference to take them out. My ~/Desktop directory is empty but icons for those two partitions are showing up anyway.

C) Just out of curiosity, why isn't my main Windows partition there as well? It's the same file system as the shared partition, they're both mounted, but Gnome didn't put it on my desktop. Not that I want it there. I'm just wondering.

Thanks!

---

### Post by taurus on 2007-10-27
Edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and change the mount point from /media/sda1 (as an example) to somewhere else like /mnt/sda1.  

Then, you need to create a new mount point for it to mount to.

```
sudo mkdir /mnt/sda1
```

---

### Post by Pumalite on 2007-10-27
Delete.

---

### Post by Excalibre on 2007-10-27
So, any way to get that stupid icon for that Dell partition off my desktop?

---

### Post by taurus on 2007-10-27
Just don't mount that partition.  Besides, you are not supposed to touch that partition because if you screw that up, you can't recovery your Windows using that partition.

```
gksudo gedit /etc/fstab
```
and place a # in front of the entry for that partition to comment it out.

Save it and reboot.

---

### Post by dmber on 2007-10-28
so what if i want to mount a drive, but not have it show up on the desktop?  

[http://ubuntuforums.org/showthread.php?t=595437](http://ubuntuforums.org/showthread.php?t=595437)

(sorry for the dupe...)

---

### Post by Drakkor on 2007-10-28
Oops, did it too,lol

---

### Post by strabes on 2007-10-28
Please mark this thread as resolved using the "Thread Tools" menu.

---

### Post by Drakkor on 2007-10-28
Is it solved ? Speaking of thread tools, my only options are:
1. Show Printable Version
2. Email This Thread
3. Unsubscribe From This Tread
4. Ignore This Thread
:confused:

---

