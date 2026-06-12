---
title: "fsck automatic check always fails - dies with status 4 but I can always fix it."
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-29
ok so after 30 boots fsck runs its check and always fails with

/dev/hda1 unexpected inconsistency
fsck died error status 4
automatic check failed. Whole load of stuff comes up about apt-get not installed and it drops you out to the command prompt. The drive is now mounted as read only.

So I type in fsck -v and of it  goes
error reading block 14057985 among many.
Attempt to read resulted in short read while doing inode scan.

At this point it asks
ignore error (y) which I reply yes.
then it asks force rewrite (y) and I reply yes. This happens about 10 times with the same blocks.

Then the system goes on to pass 2 3 etc and then  reboot and am ok again.

Until next time, 30 boots from today. Anybody got a permanent fix for this. And yes there are no bad blocks on the drive I checked.

---

### Post by philinux on 2007-08-29
anyone else suffer from this?

---

### Post by philinux on 2007-08-29
bump

---

### Post by philinux on 2007-08-30
Last time bump I guess nobody knows how to cure this one. Maybe its just doing the correct thing like scandisk would but how do you get it to automatically fix the errors?

---

### Post by irish_flu on 2007-08-30
Weird.  My first guess would indeed be "bad blocks"; what did you use to check for them?

---

### Post by philinux on 2007-08-30
Well thats it when I run fsck from diagnostic boot  it does the pass one clean. It just seems to be the routine automatic check that fails and always the same blocks. Mine seems to be set for every 36 boots.

---

