---
title: "running fsck at boot (quick question)"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by eks on 2007-08-28
Where do I find the options on "to run or not to run" fsck on boot?

What I mean is that I would like to CHOOSE to run fsck on the next boot.



eks

---

### Post by tszanon on 2007-08-28
> **eks said:**
> Where do I find the options on "to run or not to run" fsck on boot?

What I mean is that I would like to CHOOSE to run fsck on the next boot.



eks
Take a look at tune2fs, as stated here: [http://ubuntuforums.org/showthread.php?t=445584&highlight=tune2fs](http://ubuntuforums.org/showthread.php?t=445584&highlight=tune2fs)

---

### Post by mcduck on 2007-08-28
Just edit /etc/fstab and change the last number on the partition's entry line to "0" to disable automatic fsck on that partition.

---

### Post by por100pre1 on 2007-08-28
Another approach to fsck is just to run it when actually desired:

```
sudo touch /forcefsck && sudo reboot
```

---

