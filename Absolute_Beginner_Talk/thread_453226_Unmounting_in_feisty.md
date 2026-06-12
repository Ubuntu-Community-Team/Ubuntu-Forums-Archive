---
title: "Unmounting in feisty"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by BrYanwithaY1986 on 2007-05-24
I have an external hard drive with two partitions, which I use...once in a while.

I am unable to "eject" it after using it.  When I try, it says it's unable to eject it, and it opens up both partitions.

The light of the hard drive is green before I eject it (telling me that it's not doing anything), but turns blue after I try to eject it (telling me that it's writing or reading), and a message box pops up telling me that it's writing to the device, and it's therefore unsafe to remove.

It's like it tries to access the device when I try to eject it.....So I can never "safely" remove the cable (or shut of the hard drive).  

I usually just turn the computer off and then cut the power to the hard drive....which is fine, but this seems like a strange bug.

---

### Post by ruy_lopez on 2007-05-24
Make sure your terminal doesn't have its "pwd" inside any of the drives directories (sillly, I know, but I just thought I'd check).

Try changing the permissions on the mount point. If the drive mounts under "/media/drive" put this in a terminal:

```
sudo chown yourUID:yourGID /media/drive 
```

Then try to unmount again, issuing.
```

sudo umount /media/drive
```

---

