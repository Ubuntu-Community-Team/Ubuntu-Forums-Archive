---
title: "Can I use ext3 for my /boot partition?"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-07
Or must I use ext2 for the boot partition?

Thanks !

---

### Post by Xian on 2006-03-07
You can use ext3 no problem.

---

### Post by ssalman on 2006-03-07
There is no limitation on what you use for /boot, I use ReiserFS. But I would recommend to stay away from ext2 as it is not a journaled file system, and you would risk losing more data in the case of a power failur. hope this helps.

---

### Post by az on 2006-03-07
What makes you think you should use ext2?

---

### Post by Xian on 2006-03-07
[QUOTE=azz]What makes you think you should use ext2?[/QUOTE]

Probably because it sits in the Gentoo handbook and spread like the flu. :)

---

