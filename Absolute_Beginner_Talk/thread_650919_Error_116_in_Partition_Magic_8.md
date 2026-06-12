---
title: "Error 116 in Partition Magic 8"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by peterhuang913 on 2007-12-26
When I run PM8 in Windows XP, it gives me an "Error 116" error which corresponds to the partition tables. I Just install Ubuntu at add to my Windows XP and both run fine. It just that PM8 gives me an error.

Any ideas? Could it be the GRUB or whatever? During the install, it asked me where to install it and I choose use all free space. Then I selected the partition to be primary, should I have chosen to make it a logical partition?

Thanks ahead and hopefully this problem could be solved.

---

### Post by chewearn on 2007-12-27
Link:
[http://service1.symantec.com/SUPPORT/powerquest.nsf/6c360f88152ecfce88256e91005066ac/e6223d1630e8ad8388256e8d006a841e](http://service1.symantec.com/SUPPORT/powerquest.nsf/6c360f88152ecfce88256e91005066ac/e6223d1630e8ad8388256e8d006a841e)

---

### Post by peterhuang913 on 2007-12-27
I've been there. Do I really have to reinstall Ubuntu or Windows?

---

### Post by chewearn on 2007-12-27
> **#116 Partition table Begin and Start inconsistent**
The hard disk partition table contains two inconsistent descriptions of the partition's starting sector. This error can occur if the operating system reports a hard-disk geometry that is different than the geometry in use when the partition table was written. Possible causes include: (1) different operating systems reportdifferent hard-disk geometries, (2) you boot from a diskette that loads a different driver than is loaded when you boot from the hard disk, (3) upgrading the operating system causes a different driver to be used, (4) the hard disk or controller has been changed, (5) the BIOS has been upgraded, (6) the BIOS LBAsetting has been changed, or (7) there is a partition table virus present on the hard disk.

In most instances, you should resolve the problem as explained in [Resolving partition table errors]("http://service1.symantec.com/SUPPORT/powerquest.nsf/docid/2004050716430062?Open&docid=2004050712232662&nsf=powerquest.nsf&view=6c360f88152ecfce88256e91005066ac"). You can also use a virus scanning program to remove any partition table virus. Data loss is possible if the number of heads or sectors per track has changed since you first created your partitions.

It sounds to be a serious problem, which needs to be fixed (even though your OSes appeared to be running fine).  Unfortunately, I don't know enough about Partition Magic to be able to give another solution.  Or whether it is actually a bug somewhere.

---

