---
title: "External hard drive/fstab"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by schreckles on 2007-10-17
OK, so I've been trying to get the external I've got to mount normally since installing Gutsy (I'm a kubuntu user, FYI). Anyway, I want it to boot automatically (my fstab entry for it is below) but it usually only auto-mounts if I login as root, even though I'm pretty sure I have it set up right. The drive doesn't show up in the GUI at all. Even after mounting it via the konsole, using:

```
sudo mount /dev/sdb1 /media/ext
```

I have it set to auto-mount (unless I did that wrong) and to identify the drive by UUID and mount it:

fstab Entry:
```
# Entry for External drive
UUID=d9a6757d-d24b-487b-a4c8-6572e428ad0b /media/ext ext3 rw,user,auto 0 0
```

So what exactly is wrong with the settings I have for it?

---

### Post by schreckles on 2007-10-17
Oh yeah, forgot to mention, I an see the HDD fine when I go to the root folder /media/ext, where it's actually mounted, and it shows up fine when I run

```
sudo fdisk -l
```

Just not in the GUI as the HDD.

---

