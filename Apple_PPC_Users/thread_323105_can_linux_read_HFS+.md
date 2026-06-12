---
title: "can linux read HFS+?"
date: 2006-12-21
forum: Apple PPC Users
---

### Post by eewald on 2006-12-21
Can ubuntu edgy read/write HFS+ file system? 

Or vice versa: can OS X read/write ext3 file system?

I'm planning to by a Macbook and make it dualboot, but curious about interoperability...

---

### Post by sciurus on 2006-12-21
Yes and yes.

My one complaint about HFS+ support from linux is that I can't find a way to map my UID in Ubuntu to my UID in OS X.

For OS X, use [http://sourceforge.net/projects/ext2fsx](http://sourceforge.net/projects/ext2fsx)

---

### Post by eewald on 2006-12-21
ext2fsx looks like beta. i can experiment, but not with my data. :-k 

is hfs+ support in official linux kernel or does it require some obscure patch/driver/utility/hack/whatever?

---

### Post by 3rdalbum on 2006-12-21
HFS+ support is included in the Ubuntu kernel (not sure if it's actually in the kernel.org sources). I'd still recommend installing hfsplus and hfsutils from the repositories.

---

### Post by jasin on 2006-12-22
HFS is supported in linux Kernel 2.6.18 and beyond.

---

### Post by gnomeza on 2006-12-22
> **eewald said:**
> ext2fsx looks like beta. i can experiment, but not with my data.Been using ext2fsx for almost three years now. No problems.

> **sciurus said:**
> My one complaint about HFS+ support from linux is that I can't find a way to map my UID in Ubuntu to my UID in OS X.OSX UIDs start from 501, Debian from 1000. Syncing your ubuntu UID to OSX is easy.

In Ubuntu:
```
sudo usermod -u *osx-uid* *ubuntu-username* [COLOR="Green"]# change Ubuntu UID to 501[/COLOR]
```
(Your OSX UID is normally 501.)
This will also *automatically* fix the UIDs on all files in your home directory.
Files you own outside your home dir must be updated manually:
```

sudo umount /osx **[COLOR="Red"]# UNMOUNT OSX PARTITION FIRST!!![/COLOR]**
sudo find / -uid *old-ubuntu-uid* -print0 | xargs -0 chown *osx-uid* [COLOR="Green"]# change file permissions[/COLOR]

```

That last line is destructive. (Get it wrong and you can break your system.)

---

### Post by eewald on 2006-12-22
big thanks for help! 8)

---

### Post by KaOS-bEat on 2006-12-23
one last note: to write to a hfs+ partition in linux, you need journaling to be off. To do this disable it in the OSX diskutil

KaOS

---

