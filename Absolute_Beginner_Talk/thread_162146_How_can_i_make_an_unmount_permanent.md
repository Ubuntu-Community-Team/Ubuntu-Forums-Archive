---
title: "How can i make an unmount permanent"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2006-04-18
Hi, I have windows on a second partition on my first harddisk, and since its NTFS I can't use it in Ubuntu, so I unmount it every time (I don't like rubbish on my desktop).
Is there a way to make such an unmount permanent?
I know this can be edited in:
```
sudo gedit /etc/fstab
```
but i don't know what option i have to use to make sure it doesn't get mounted again.

the line in fstab about that disk is:
/dev/hda1       /media/hda1     ntfs    defaults        0       0

---

### Post by aysiu on 2006-04-18
[QUOTE=Ecthelion]
/dev/hda1       /media/hda1     ntfs    defaults        0       0[/QUOTE] Just delete this line. That's it.

By the way, you *can* use it in Ubuntu, you just can't write to it. You can read off it just fine if you change the line to read ```
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0
```

---

### Post by Ecthelion on 2006-04-18
So i can read from it....
I didn't knew that...
Thanks, that's even better than permanent unmount!

---

