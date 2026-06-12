---
title: "problem formatting external HDD"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by synthsrkl on 2007-01-09
been on ubuntu a few months now and every problem so far i've been able to solve either on my own, or through the wonderful help from questions already posted on this forum!

alas now i need some help that i couldn't find.

i have a 250GB external harddrive which i have backed up and am ready to format for the simple reason that i can't write to it, only read, probably becuase it's NTFS.

anyway i tried formatting using gparted but when i right click to format, the option is greyed out.

i want to format it to FAT32

can anyone help me?

---

### Post by taurus on 2007-01-09
You first need to unmount it before you can format it!  Did you mount that harddrive somewhere?  This little command will tell you if it is mounted and where it is mounted to.

```
df -h
```

---

### Post by adewale on 2007-01-09
i think there are other options something like ntfs-3g should give you write access to your ntfs partition

---

### Post by synthsrkl on 2007-01-09
thanks alot! all solved now

we were all noobs once!

i tried the unmount method and it worked, thats for your input too though adewale

---

