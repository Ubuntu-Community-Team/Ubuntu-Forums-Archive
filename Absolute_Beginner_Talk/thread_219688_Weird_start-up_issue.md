---
title: "Weird start-up issue"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by eulipion2 on 2006-07-20
Hello,
I just installed Xubuntu yesterday, and whenever I startup I get this:
```
fsck.ext2: Bad magic number in super-block while trying to open /dev/hda2
/dev/hda2:
The superblock could not be read or does not describe a correct ext2 
filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something 
else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:  
e2fsck -b 8193 <device>

* File system check failed.  Please repair manually.
* Control-D will exit from this shell and continue system startup.
```
What do I use for <device>?

Thanks!

---

### Post by ThrobbingBrain66 on 2006-07-20
someone please correct me if i'm wrong, but the <device> is refering to the drive or partition that you needs to be checked.  so i think the command would read:

```
sudo e2fsck -8 8193 /dev/hda2
```

like i said, i'm not sure, so you might want to wait for someone more familiar with this to respond.

---

### Post by malkaven on 2006-07-20
getting the same error myself.  not sure how to fix it.  ill post here if i come accross a fix.

---

### Post by malkaven on 2006-07-20
Fixed my issue,

[http://forums.gentoo.org/viewtopic-t-480789-highlight-superblock.html](http://forums.gentoo.org/viewtopic-t-480789-highlight-superblock.html)

I went into my fstab

sudo nano /etc/fstab

and deleted the /boot line like mentioned in that post.  worked for me.  Hope it works for you bro:)

---

### Post by nalmeth on 2006-07-20
If you're running e2fsck or fsck you should always do these unchecks on UNMOUNTED VOLUMES!! SERIOUS DATA LOSS POSSIBLE OTHERWISE

Boot up a liveCD like knoppix or something, don't do this logged into ubuntu.

---

