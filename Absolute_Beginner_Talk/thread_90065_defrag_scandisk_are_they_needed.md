---
title: "defrag? scandisk? are they needed?"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by UbuntUser4389 on 2005-11-14
Are there the same system programs in Linux as there are in Windows?? I am talking about a certain few, Defrag, and Scandisk. Does Linux have such programs (or like programs), or is it so effecient that it doesn't need such programs (and that would not surprise me!). 

Thanks a TON!

---

### Post by Gustav on 2005-11-14
Linux doesn't need defrag at least and it does the equivalent of scandisc every 30:th time you start your computer (or something like that).

---

### Post by kont.raen on 2005-11-14
[QUOTE=UbuntUser4389]Are there the same system programs in Linux as there are in Windows?? I am talking about a certain few, Defrag, and Scandisk. Does Linux have such programs (or like programs), or is it so effecient that it doesn't need such programs (and that would not surprise me!). 

Thanks a TON![/QUOTE]

Hi,

well actually it depends much on which filesystem you are using. In general, filesystems that are available for *NIXes are much less prone to fragmenting files - but the closer they get to 100% disk usage, the more likely they are to fragment files (a matter of pure logic). IIRC ext2/ext3 for example are known to heavily start fragmenting files, if the disk usage of a given partition rises above 80% or some such.

Which tools you have in order to correct fragmentation and check a partition's consistency again depends on which filesystem you are using.  You can get a short info on that if you key up the respective man page (e.g. man xfs) and have a look in the "see also :..." section.

---

