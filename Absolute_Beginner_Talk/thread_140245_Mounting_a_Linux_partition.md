---
title: "Mounting a Linux partition?"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by MrChips on 2006-03-05
I am currently dual booting between two distros of Linux.  One being Ubuntu (normal operations) and the other being Agnula/Demudi (music production).  Agnula does not have samba support so I have no way of sharing files with Windows.  Ubuntu does...

So how would I mount a partition of Agnula within Ubuntu to access music files?  Even so it would be easier that booting back and forth anyway.

---

### Post by aysiu on 2006-03-05
This is another Linux partition on the same computer?
Just create a mount point and add it to your /etc/fstab file.

Let's assume your other partition is /dev/hda2.
```
sudo mkdir /agnula
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Then add this line in ```
/dev/hda2 /agnula ext3 defaults 0 0
``` Save (control-x), confirm (y), and exit (Enter).

That assumes, of course, that Agnula's on /dev/hda2 and that it's Ext3 (as opposed to Reiserfs).

---

### Post by Herman on 2006-03-05
Sorry, simultaneous post with aysui, use aysiu's method, he is better at this than me.

---

### Post by MrChips on 2006-03-05
Well that was simple enough. :)

The folder was there in the directory but nothing was in it until I rebooted.  Now it has become a reality! 

This will save loads of disc space carting .wav files on one comp between 2 OS's.

Thanks!:KS

---

### Post by Sutekh on 2006-03-05
[QUOTE=MrChips]
The folder was there in the directory but nothing was in it until I rebooted.[/QUOTE]
For future reference, Ubuntu does not require reboots for something like that
```
sudo mount -a
``` would remount all partitions, saving you a reboot.

---

