---
title: "remove other partitions"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by ieee488 on 2007-01-03
I have Windows 2000, OpenSUSE 10.1, Ubuntu 5.10, and Ubuntu 6.06 quadruple-booting
on my PC.

I want to keep Windows 2000 and Ubuntu 6.06 and free up the space taken up by the other
distros.

Could someone point me in the right direction to do this?

Thanks in advance.

---

### Post by bodhi.zazen on 2007-01-03
I would advise Gparted:

	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by K.Mandla on 2007-01-03
Ditto that. GPartEd is perfect for that.

---

### Post by bigken on 2007-01-03
Yep Gparted liveCD and very easy to use ;)

---

### Post by ieee488 on 2007-01-03
great!

Does GParted know what to do with the GRUB menu?
I'm worried about being left with entries to deleted partitions.

---

### Post by bodhi.zazen on 2007-01-03
> **ieee488 said:**
> great!

Does GParted know what to do with the GRUB menu?
I'm worried about being left with entries to deleted partitions.

No but boot to Ubuntu and then:```
sudo update-grub
```

Or edit /boot/grub/menu.lst manually ....

---

