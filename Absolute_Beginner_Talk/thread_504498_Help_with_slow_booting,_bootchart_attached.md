---
title: "Help with slow booting, bootchart attached"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by newbiboy on 2007-07-19
Hello! I'm new at linux and i have no idea why the installed ubuntu 7.04 takes around 10 mins to boot up. This problem does not exist when i use the live cd. Could anyone give any advice for the problem? Thank you

---

### Post by DBStevens on 2007-07-19
Cool chart, how about posting the output from:

dmesg

and

cat /proc/mtrr

---

### Post by Atomic Dog on 2007-07-19
Open up /etc/network/interfaces and clear out everything except the following:

```
auto lo
iface lo inet loopback
```

(backup the interfaces file first)

This solved my slow boot issue in Feisty.  There is a fair chance your issue is related, and I do not believe any negative effects happen because of the change.

---

