---
title: "How do I install kernel headers/source?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by S3loth on 2007-12-26
I'm getting errors while installing [this]("http://masscat.afraid.org/ninds/rt2570.php"), so it says to install the kernel headers/source.

---

### Post by PmDematagoda on 2007-12-26
The kernel headers can be installed using:-
```
sudo apt-get install linux-headers-kernelversion
```

The kernel source can be installed using:-
```
sudo apt-get install linux-source-kernelversion
```

The kernel version can be obtained using:-
```
uname -a
```

---

