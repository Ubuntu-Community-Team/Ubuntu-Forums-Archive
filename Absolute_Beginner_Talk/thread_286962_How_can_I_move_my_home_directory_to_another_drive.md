---
title: "How can I move my home directory to another drive"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by lift_test on 2006-10-28
It's a hangover from windows.  I always have OS on one drive and all my data files on another (I have this problem "I wonder what happens if I push this, O shit!").  Consequently I would like to do the same in Ubuntu so that I can reload OS when I "bend" it without having to reload all my data.

---

### Post by llamakc on 2006-10-28
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by stupidkid on 2006-10-28
Mount another dirve to /home. Add it to /etc/fstab. For example

```
/dev/sdb1               /boot           ext2            noauto,noatime  1 2
/dev/sdb2               /               ext3            noatime         0 1
/dev/sdb3               /usr            reiserfs        noatime         0 2
/dev/sdb5               /home           ext3            noatime         0 2
/dev/sdb6               none            swap            sw              0 0
```

---

### Post by lift_test on 2006-10-28
> **stupidkid said:**
> Mount another dirve to /home. Add it to /etc/fstab. For example

```
/dev/sdb1               /boot           ext2            noauto,noatime  1 2
/dev/sdb2               /               ext3            noatime         0 1
/dev/sdb3               /usr            reiserfs        noatime         0 2
/dev/sdb5               /home           ext3            noatime         0 2
/dev/sdb6               none            swap            sw              0 0
```

Thanks, but it doesn't mean anything to me, I can use command line in DOS quite happily but have never done it in Linux and don't know where to start.

PS The drive I want to move home to is a phsically separate drive.

---

### Post by stupidkid on 2006-10-28
That's fine, what is the name of it? I'm guessing /dev/hdb1 or something (I'll assume its /dev/hdb1)? Is the drive formated? If not format it to ext3. The just add 
```
/dev/hdb1               /home           ext3            noatime         0 2
```

To your /etc/fstab. Acutally it would be better if you mount /dev/hdb1 somewhere first, say /mnt/hdb1 and copy all the stuff in /home/ there first. Don't copy the actual /home directory, the only directory(s) in /mnt/hdb1 should be the home folders of your users.

---

### Post by confused57 on 2006-10-28
Instead of a separate home, you might just want to mount the drive to store data on it:
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

See the sections for "Mount Linux" if it's formatted ext3, or
"Mount Windows" if it's FAT.

---

### Post by lift_test on 2006-10-29
Thanks all, have manged to do it.

---

