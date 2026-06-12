---
title: "etc/fstab"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-03-04
I was mucking about with etc/fstab and i think I've knackered it. I'm being told that line 4 is rubbish :
/dev/scd0 /mnt/auto/cdrom udf, iso9660 ,ro,owner,noexec, noauto 0 0

I'm using Damn Small linux and i can't remember what i changed - I know I'm an Idiot

Can anyone spot the error or does anyone know what the original file looked like!

Thanks

---

### Post by PeterJS on 2008-03-04
Looks like you've got whitespace between iso9660 and udf in your fs list, and between the noexec and the noauto in the options list, and an extra comma before the ro. Try removing that and seeing if that makes it happy.

---

### Post by mali2297 on 2008-03-04
Try
```

/dev/scd0    /mnt/auto/cdrom    udf,iso9660    ro,owner,noexec,noauto   0   0

```

Check that the directory /mnt/auto/cdrom exists.

---

### Post by the beak on 2008-03-04
Thanks

---

