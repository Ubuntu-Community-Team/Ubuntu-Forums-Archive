---
title: "File System Check failed !"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-10-26
Ok , getting that error when booting, I can hit exit,and reboot to the system,the error in question is another drive that I just formatted to ext3 with GParted, but it's no showing up
as mounted. here's the log: fsck.ext3: Unable to resolve 'UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7'

/dev/sda2: clean, 3748/6766592 files, 6835296/13530746 blocks
fsck died with exit status 8
 Help !! :confused:

---

### Post by Dr Small on 2007-10-26
Maybe try:
```
fsck /dev/sda2
```

---

### Post by rsambuca on 2007-10-26
No problem.  All that happend is the UUID changed after you formated the partition.  As a result, the UUID in your existing fstab doesn't match the new one.  To correct this, you can get the new UUID for the partitions using either one of ```
blkid
```or ```
ls /dev/disk/by-uuid/ -alh
```

Then edit your fstab using```
gksudo gedit /etc/fstab
```

Just correct your fstab to the new UUID that has changed.  An alternative is to just get rid of the UUID's altogether and replace it with the conventional /dev/hda2, etc.  Both will work.

UUID's come in handy for external drives.

---

### Post by MegaJim on 2007-10-26
edit: beaten!

check the disk's UUID hasn't changed

```
 sudo vol_id --uuid /dev/????
```

and replace the ???? with your device

---

### Post by Drakkor on 2007-10-26
Hey, rsambuca, Thanks !! :) that worked like a charm, no errors on rebooting now !!
Man, I redid grub,checked fstab, grub menu.lst and it all was driving me nuts,lol !

---

