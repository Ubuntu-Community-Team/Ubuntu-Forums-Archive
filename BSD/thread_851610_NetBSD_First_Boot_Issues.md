---
title: "NetBSD First Boot Issues"
date: 2008-07-06
forum: BSD
---

### Post by Tubes6al4v on 2008-07-06
Hey guys,

I am trying to install NetBSD on the second hard drive of my HP dv9000. I chose NetBSD because it supposedly works well with 64bit architectures. I partitioned my 120gb hard drive to have two 20gb ext2 file systems and the rest unformatted.

I installed NetBSD on the first partition of that drive with the option of a NetBSD Filesystem. I did not install the Bootloader so that I could load all my OS's from my Ubuntu Grub Menu.

Here is my Net BSD Entry in Grub:

```
 
title            NetBSD 64-bit
root             (hd1,0)
chainloader +1
```


Ok, I think that just about covers the set up: When I boot into NetBSD green code indicates that everything is loading. right after loading my Keyboard I get this output and everything freezes:
```
pmsprobe: reset response 0xfa
```


Anyone have a suggestion?

---

### Post by cardinals_fan on 2008-07-07
That's odd... I'll look into it once I get my box up and running again.

---

