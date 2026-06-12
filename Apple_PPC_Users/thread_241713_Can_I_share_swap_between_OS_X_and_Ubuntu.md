---
title: "Can I share swap between OS X and Ubuntu"
date: 2006-08-22
forum: Apple PPC Users
---

### Post by kulath on 2006-08-22
I want to have a dual-boot Mac OS X/Ubuntu system.

I haven't yet installed Ubuntu, but I understand that it creates a swap partition.

Can I use the Ubuntu swap partition for Mac OS X as well?

What filesystems do the respective systems require for their swapspace, and are they incompatible?

(iMac iSight G5)

---

### Post by sciurus on 2006-08-24
OS X uses swap files on the HFS filesystem afaik.

---

### Post by kulath on 2006-08-25
Mac OS X does indeed use normal files within the filesystem for its swapspace (basically /etc/rc says 'swapdir=/private/var/vm'). There are several recipies for moving OS X swap to another partition.

My question thus probably resolves to whether the Linux swapspace can be a normal filesystem that can be mounted in th enormal way by Mac OS X.

---

### Post by hajk on 2006-08-25
I don't think that it could be a "normal file", as you call it. Even in Linux you can use a swap file (instead of a swap partition), and you'll have to
make that swap file an image that can be mounted. In the directory that will contain the swapfile use the following commands, 

$ sudo dd if=/dev/zero of=swapfile bs=1024 count=132207
$ sudo chmod 600 swapfile
$ sudo mkswap swapfile
$ sudo swapon swapfile 

depending on the size of the swap file. Now you must also add the swapfile
(with full path) to /etc/fstab.

Mind you, this would be in Linux -- OS X doesn't use /etc/fstab, so you 
would have to find out how to do this in OS X. Since Darwin is now based on FreeBSD, one would expect it to be possible... ask around on a Mac OSX/Darwin newsgroup, I would say.

---

