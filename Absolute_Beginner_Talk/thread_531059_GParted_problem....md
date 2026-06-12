---
title: "GParted problem..."
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Ozcu on 2007-08-21
It doesn't allow to resize my partition, and when I try to unmount, it says I should do it manually, how do I do it? :$

I need ~30GB for Windows

---

### Post by Skrynesaver on 2007-08-21
You may need to boot from a live CD first as you can't unmount the base filesystem ;)

If all your filesystems are already mounted you can unmount them using the umount command (man umount), which is called as follows to unmount the second and third partitions from the first IDE disk
```

umount /dev/hda2
umount /dev/hda3

```

---

### Post by dptxp on 2007-08-21
Maybe you can download GParted, make live CD, boot with it and partition.
The GParted CD is quite useful.

---

### Post by LaRoza on 2007-08-21
I recommend the Live CD also, the link is in my sig.

---

### Post by Blara on 2007-08-21
I have a similar problem, but not quite the same...

I went from windows to Ubuntu, and at the time I had 2 partitions I installed Ubuntu on one and just went on and put the whole / on the first partition, leaving the other untouched. But now I would like to have the second partition as my /home, I've recently formated it from NTFS to ext3, but now I don't know how to migrate my /home folder onto that newly made partition. Anyone able to help?

---

### Post by mxg01 on 2007-08-21
Try this:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Read it through a couple of times though as you need to be sure of what you are doing.

---

### Post by Blara on 2007-08-21
> **mxg01 said:**
> Try this:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Read it through a couple of times though as you need to be sure of what you are doing.

Thank you

---

