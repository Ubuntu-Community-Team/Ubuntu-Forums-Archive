---
title: "LVM Basic help please"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Canarygsr on 2007-08-30
Ok, I have swearched for a few weeks but I am obvioulsy looking in the wrong spot.

Im a ubuntu newb, I have managed to mount a LVM in terminal and put it in fstab so it loads at boot. My problem is I dont have write access to the base directory of the mounted partition.

how can I change the write access?

some other info
I can write to any of the folders in the mount
The LVM was created in fedora and has all my mythtv files in it

thanks if anyone can help

Nick :)

---

### Post by HermanAB on 2007-08-30
Read the fstab man page and add 'rw' or use 'defaults' in the options.

Cheers,

H.

---

