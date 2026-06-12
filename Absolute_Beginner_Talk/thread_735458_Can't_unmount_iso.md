---
title: "Can't unmount iso"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by ClearyA on 2008-03-25
Ok its driving me crazy... i mounted an iso on cdrom0 with gmount-iso and it will not let me unmount it it says readonly and its driving me crazy. i cant get rid of it

---

### Post by bubba_169 on 2008-03-25
Try opening a terminal and typing:

```
 sudo umount /media/cdrom0
```

That has worked for me before. Failing that a reboot should do the trick :)

---

### Post by Shazaam on 2008-03-25
Worth a try (I know it's an iso)........
```
sudo umount /media/cdrom0
```
and if it says device is busy try this.......
```
sudo eject
```

A hint (re-open gmountiso)........
[https://bugs.launchpad.net/ubuntu/+source/gmountiso/+bug/201545](https://bugs.launchpad.net/ubuntu/+source/gmountiso/+bug/201545)

---

