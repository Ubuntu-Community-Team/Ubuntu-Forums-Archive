---
title: "Where to install"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by backflip on 2007-11-15
I've already had to re-install windows today so I'd rather not cock-up the ubuntu installation again. The 'guided' installation option shows windows on hdb1 on partition 1 (although I opt for manual install) but when I click on 'advanced' at the final step before install(with partitions 2,3,&4 for /, swap & home)  grub wants to load on hdb0. I don't know how windows is seen as being on a partition on hdb1 and I'm at a loss where to install grub to, there or hdb1.
Thanks in advance.

---

### Post by jken146 on 2007-11-15
Installing GRUB on hdb0 should be fine.

---

### Post by Duck2006 on 2007-11-15
This may help

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by backflip on 2007-11-15
I've already successfully installed ubuntu on my laptop, but the thing which still concerns me with the desktop is that grub wants to install on hdb0, when windows is on hdb1. I checked the partitions with gparted and windows is definitely on hdb1. I can't see hbd0 anywhere, and certainly windows isn't on it.

---

### Post by StephUb on 2007-11-15
If you don't know what is hdb0, then let it go to hdb0,
Do not try to put grub on the hdb1, that's where windows is....
so let go without advanced options because you're gonna mess up everything...

By the way hdb0 is the MBR of your (second ????) HD for what i'm remembering....

---

