---
title: "[SOLVED] Odd/Random Permissions"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-12
1.) I'm mounting another partition using fstab, but some files I can change and some I cannot. How do I really gain controller over these? (See attached screen shot)

```
/dev/sda6        /media/sda6      vfat   defaults,users,umask=000,fmask=111          0               0
```

---

### Post by Paqman on 2008-01-12
Looks like different directories have been given different permissions. If that's the case you can change them all by using:
```

sudo chmod -R *permissions* *directory*

```

That'll change the permissions for all directories and files beneath the one you specify. Obviously, use with care (but on a folder containing only data getting it wrong is easily reversible)

---

### Post by Malta paul on 2008-01-12
Hope this reference is of help to you:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)
Paul:)

---

