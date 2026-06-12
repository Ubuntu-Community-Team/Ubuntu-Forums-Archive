---
title: "NTFS-Access from boot-CD"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by ubtraut on 2007-10-25
Hi all,

I just got an Ubuntu 7.10 CD

Is it possible to get NTFS-Access directly from the boot CD, without installing Ubuntu and NTFS-3G?

I'd expect to see my hard disks immediately when inserting a boot CD like this.

---

### Post by julian67 on 2007-10-25
I'm not sure that you would get write access on NTFS from the live CD, I haven't tried this with Ubuntu live,  but you should be able to to mount and read the disks.

If you need NTFS write access from a live CD then Knoppix is probably the easiest. In recent versions of Knoppix you can just enable NTFS write access from a context menu (right click over the drive icon).

---

### Post by jboy012000 on 2007-10-25
Hi,

You can look at the NTFC drives on your computer with the live cd you can also load files from them but you can't write to them.

Hope this helps.

Cheers

---

### Post by ubtraut on 2007-10-25
Thanks,

read access would be better than nothing, although write access IMHO is essential.

However, how do I find the drives? On MacOSX I'd have to check below /Volumes. The USB stick  was there immediately, while I have no clue yet where "C:" would be...

---

### Post by blair on 2007-10-27
your hard drive can be found under the /media directory. Click on Places > Computer. When the file browser window opens, select Computer. You should see your hard drive listed and can double click on it. You may have read/write permission that you'll need to address. I'm having that problem now. I can copy off some files but not others. Instead of trying to fix that however, it is simply easier for me to use my Knoppix CD instead where I can simply mount it automatically as read only and then with a single mouse click change that to read/write.

---

