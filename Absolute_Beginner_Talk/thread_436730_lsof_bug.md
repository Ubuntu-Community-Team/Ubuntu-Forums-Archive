---
title: "lsof bug?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by slamdunk on 2007-05-08
Hi,

I use lsof like this:

lsof /dev/hdaXXX

where hda is my partition (home or root)

but it returns nothing. In Edgy Eft or other distributions it works.

Is it a bug on lsof for Feisty?

Thanks,
Alex

---

### Post by LaurelLynn on 2007-05-08
/dev/hdaXXX  refers to the device driver.  I would be surprised if lsof worked with the driver. I would thing the command needs to be run on the mount point.  It should either have an entry in /etc/fstab, or mount to the /media directory as  /media/hdaXXX

---

### Post by slamdunk on 2007-05-08
From lsof man:

To list all open files on device /dev/hd4, use:

              lsof /dev/hd4


you get all files open in that partition using "dev" instead of "/home/user" etc

Alex

---

### Post by Skrynesaver on 2007-05-08
```
lsof +D /media/mountpoint
```

---

### Post by slamdunk on 2007-05-08
Yes I know "+D" option but why is not working for "/dev"?

---

### Post by hartz on 2007-05-08
lsof really only works with the mountpoint, as suggested by LaurelLynn.  However because in Feisty you have a different mounting syntax, lsof is unable to "translate" the device which you are specifying back to the mountpoint, as it did on Edgy (In Edgy mounting was usually done using /dev/hdX entries while in Feisty it has changed to using the UUIDs)

It would appear that lsof did some clever stuff to use the device name to determine to the mountpoint, and that doesn't work with the UUID mounting used in Feisty....

Or at least that is my guess....

I didn't know you could use lsof against the device.  It doesn't seem like a stable feature in any case.

---

