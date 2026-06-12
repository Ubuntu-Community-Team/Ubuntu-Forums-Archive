---
title: "Buring a non udf dvd"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by littletinman on 2008-02-18
Hey everybody,

  How do i burn files onto a dvd from a windows cp such that the file format is not UDF. I want my ubuntu CP to be able to read them.

---

### Post by c-ron on 2008-03-30
Ubuntu reads discs in both ISO9660 and UDF formats.
Your definition for your DVD drive in /etc/fstab might be borked.
See: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233)

---

