---
title: "Mount ext3?"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by SSamiK on 2006-07-22
How do I mount a ext3 partition so that it's read/writeable? 

From my fstab:

/dev/hda3 /media/movieclips   ext3   defaults   0   0

This leaves the partition as read only, so what should be changed?

:confused:


SOLVED: Had to change permissions on mount point. :rolleyes: 

sudo chown -R user:user /media/movieclips
sudo chmod -R 755 /media/movieclips

---

### Post by SkyNet2029 on 2006-07-22
From my /etc/fstab, adding the rw after defaults allows read/write access

```
/dev/hda3 /media/movieclips ext3 defaults,rw 0 0

```

---

