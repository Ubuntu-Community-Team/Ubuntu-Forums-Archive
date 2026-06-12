---
title: "File System Check Failed [Resolved]"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-04-30
Hi Guys,

I've just had to reinstall Grub (that's all worked ok, Grub menu restored and working nicely), and now I have a problem.  I don't know if the two are linked but I offer that information just in case.

Whenever I boot I now get a message telling me that the 'File System Check Failed' and point me at a log in /var/log/fsck/checkfs

The entries in the log are:

```

Log of fsck -C -R -A -a 
Mon Apr 30 15:07:24 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=8b5331c2-7ef5-4429-b42b-a5ed30d18c7c'

fsck died with exit status 8

Mon Apr 30 15:07:25 2007
----------------

```

I don't even know where to start to fix this, so any help would be gratefully received.

Thanks.

---

### Post by Catsworth on 2007-04-30
Should probably have said that when the boot fails I am given a 'root' terminal, if I type 'exit' there Ubuntu boots normally.

---

### Post by NilsE on 2007-04-30
It looks like the UUID in the GRUB menu or fstab does not match the UUID of the drive it is pointing to. 

If you are not getting to ubuntu because of this you can boot up with the liveCD and look at the UUID of the drives and make sure it is the same as what is in your grub menu and fstab. The key is to make sure all 3 match for that partition.

---

### Post by Catsworth on 2007-04-30
Ok, I sort of understood that :)

The UUIDs don't appear in Grub but they do (obviously) in /etc/fstab.

How can I find out what the UUIDs *should* be, where will I find that information in Ubuntu?  The only place I can ever remember seeing it is in /etc/fstab.

Thanks.

---

### Post by Catsworth on 2007-04-30
Sussed it.

Browsed the file system through /dev/disk/by-uuid and checked what each mounted UUID was linked to, found the one that didn't match and edited /etc/fstab.

All is rosey again now :)

Thanks for your help :)

---

