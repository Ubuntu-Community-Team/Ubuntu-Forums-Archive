---
title: "Completley removing Ubuntu"
date: 2009-08-24
forum: Apple Hardware Users
---

### Post by shade11 on 2009-08-24
I recently installed 9.04 on my Macbook Pro 5,5. I was not very fond of it on my laptop as I found it preferable to run Ubuntu on my desktop instead.

What I would like to do is to have my entire hard-drive set back to OSX. I already deleted the Ubuntu partition(s) and all that's left is my OSX (and EFI) partiton as well as a bunch of blank space past it. As all should know, the OSX partition is formatted as HFS+.

I've attempted to restore my partition back to its original state via bootcamp and gparted, but no luck. (i am not talking about restoring backed up data) Is there a way to fix this?

---

### Post by tuxxy on 2009-08-24
So you want to use that free space to expand your OSX partition? this can be done using a Live CD and running gparted.

---

### Post by shade11 on 2009-08-24
> **tuxxy said:**
> So you want to use that free space to expand your OSX partition? this can be done using a Live CD and running gparted.

gparted refuses to expand an HFS+ partition.

---

### Post by aermartin on 2009-08-25
you might have to use the install DVD for OSX and just remove the partitions and make one solid and reinstall OSX.

I guess you know how but boot with the CD and press C, while in the installer go to disk-utility and delete partitions. and make a new one

---

