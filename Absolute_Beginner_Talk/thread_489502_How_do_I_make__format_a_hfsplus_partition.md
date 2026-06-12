---
title: "How do I make / format a hfsplus partition?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by grim1234 on 2007-07-01
Does anyone know how to make a hfsplus filesystem on a partition from ubuntu?

If not, any other way to do it? (disk utility doesn't let you do just one partition).

Thanks!

---

### Post by stmiller on 2007-07-01
What exactly are you trying to do? Linux can read/write HFS+ partitions, but cannot create them. The program gparted works to make partitions, so poke around with that.

---

### Post by grim1234 on 2007-07-01
Update

I could not create a partition in disk utility from osx after using boot camp. So I used cfdisk to create a partition and set it to type AF. Then by booting the osx install cd and using the disk utility from there I could create the hfsplus partition (no journaling). disk utility on the osx install could not be used until the partition was formatted via the osx install cd. strange, something to do with boot camp probably.

No I just have to figure out permissions for mounting it via fstab.

---

