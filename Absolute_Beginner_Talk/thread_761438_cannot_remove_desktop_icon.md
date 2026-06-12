---
title: "cannot remove desktop icon"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by scientist1971 on 2008-04-21
I tried to shrink my ntfs partition (only my girlfriend uses windows now and even then only word) everything else is done better by ubuntu:)
could not shrink the partition as windows was apparently still running!
I will uses the live CD to resize but at the moment the CD drive is broken:( anyway thats not my problem...
..my main issue is that my lovely wallpaper is being ruined by a drive icon!
when I try to unmount it I get this message:
You are not privileged to unmount the volume 'S3A2913D001'.
only root can unmount

obviously this is the main drive and cannot be unmounted but I would like to get rid of the icon for aesthetic reasons
any help removing this icon (and not the drive) would be appreciated

---

### Post by lizzard on 2008-04-21
Run "gconf-editor" (Alt-F2) and go to ->apps -> nautilus -> desktop. There you can untick "volumes_visible" and everything should be fine.

---

### Post by scientist1971 on 2008-04-21
thanks lizzard worked like a treat

---

### Post by T-Virus on 2008-04-21
If you really want to unmount that drive you need root access (that's what ubuntu was asking for you when you tried to remove it).

Run terminal:

```
sudo nautilus
```

Find your desktop in nautilis and try unmounting that NTFS drive now.

Cheers. :)

---

