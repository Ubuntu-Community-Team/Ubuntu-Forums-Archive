---
title: "hdd partitions"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Compact on 2006-09-26
Is it possible to make a partition in the hard disk where I have installed the Ubuntu without erasing anything?. The hdd has 80 gb and it is about  10 % used. I would like to make a partition of 40 gb in this hdd.

---

### Post by xpod on 2006-09-26
Is the unused space unallocated or just unused?
I dont see why you cant run gparted either from it`s own live cd or from the ubunto live cd and either create the partition you require or resize your existing partition to create space for it.

Im not 100% sure about the resizing option but somebody will tell us:D

---

### Post by pseudonym on 2006-09-26
From my own experience, I don't recommend partition resizing. I tried it a couple of times on reiserfs partitions and it either just refused to resize or errored out badly (which I guess is the same thing).

If it's unallocated space you don't need to partition it from a live cd. You can just run gparted etc. from within Ubuntu.

---

### Post by xyz on 2006-09-26
Save what you have on your "10 % used" and try...vamos...nothing like experience!
That way you won't lose any of your data. Hola Barcelona!

---

