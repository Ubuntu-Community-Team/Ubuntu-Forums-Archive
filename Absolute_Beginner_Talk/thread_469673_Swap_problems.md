---
title: "Swap problems"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ggaaron on 2007-06-10
```

# /dev/hdc1
/dev/hdc1                                 none            swap,pri=2  sw              0       0
# /dev/sda2
/dev/sda2                                 none            swap,pri=1  sw              0       0

```

This is part of my fstab file. But ubuntu tells me on boot:
```
mount point none does not exist
```
Or something like that.

swapon -a does nothing, but swapon /dev/hdc1 && swapon /dev/sda2 works well... what is wrong then? What are the boot errors I get?

---

### Post by mahiyar on 2007-06-10
It seems to be hand made swap lines. I do not know the exact problem, but in my case after updating kernel ntfs partition wont mount. Turns out that if you have ide and sata mix among your drives, the latest update changes them. See the output of >>sudo fdisk -l and check them with your swap lines.

---

### Post by ggaaron on 2007-06-10
Ok, pri option was in wrong place=/

Sorry, strange though that direct swapon didn't have any errors... I've always thought that it uses options in /etc/fstab if they are available, it seems that it doesn't.

---

