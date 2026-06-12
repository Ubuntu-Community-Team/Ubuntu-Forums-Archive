---
title: "usb key mounts read-only,"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by (((X))) on 2008-03-21
This is what happened:
Yesterday I unplugged my usb key out of my computer without safely removing it first.
That was dumb

Today I was able to see all my documents on it, read-only
I was away from my computer for an hour, plugged in again, ow can't see none of my documents on it, only SETTINGS.DAT(read-only) survived.
When I plugged this usb key in my other ubuntu, they were there, but I couldn't view them in nautilus, they were just blank.

Only this usb key mounts read-only, tried 3 other, they do work.
So I don't think I need to edit mtab or fstab

These documents are very important to me.
How do I recover them, need tips.

---

### Post by dstew on 2008-03-21
You will probably have to do some file system repair on it. What type of file system does it have? FAT16 maybe? If so, you can use a Windows file system repair utility. The fsck linux program might also work.

---

### Post by (((X))) on 2008-03-21
I installed this tool
[http://www.z-a-recovery.com/](http://www.z-a-recovery.com/)
But, it recovered almost nothing, so I go type everything again.

Have tried fsck..fsckvfat, ..dosfsk..none of them worked for me.

Thanks for  tip

---

