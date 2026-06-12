---
title: "formatting"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by harrydee on 2006-08-18
I have just installed Ubuntu onto my new computer OK but need to check if the discs are NTFS rather than FAT,and change as needed. Any advice would be appreciated.:-?

---

### Post by Klaidas on 2006-08-18
umm, you could use Gparted, 
```
sudo apt-get install gparted
```

But what are you exactly tying to do?
If you installed Ubuntu, it's probably ext3

---

### Post by givré on 2006-08-18
linux use differents filesystem than microsoft'ones (which are not open source). Ubuntu use by deault the ext3 filesystem, which is as good, and probably better than NTFS.
But you'll not be able to nativly read it from windows. To do that, check [http://fs-driver.org/](http://fs-driver.org/)

If you want more info : [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

