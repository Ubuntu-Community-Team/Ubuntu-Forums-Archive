---
title: "modules directory in ubuntu"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-11-01
I just finished making nin_rt2570.ko for my nintendo wifi connector and the instructions im going by for getting it to work tell me to copy and place the file into my modules directory, and then run depmod -a. Unfortunately they compiled this for an earlier version of the kernel and since then the directory structure has changed, for instance they reference their module directory as ...

/lib/modules/2.6.14-2-k2/misc

This doesnt exist in Feisty Fawn so im not quite sure where I need to place the file. The guide im using is here: [http://masscat.afraid.org/ninds/rt2570.php](http://masscat.afraid.org/ninds/rt2570.php)

And all I really need to know is where in my modules directory I should place the file so it can load the usb device properly. Thanks!

---

### Post by Arthur Archnix on 2007-11-01
```
locate /lib/modules
```

What does this return?
```
uname -r
```

---

### Post by devosion on 2007-11-01
2.6.20-16-generic

Im sorry I should have posted the kernel version along with the first post. :(

---

### Post by Arthur Archnix on 2007-11-01
Did you notice this?
> MPORTANT NOTE: The current version of the hacked driver is based on the rt2x00.serialmonkey.com v1.1.0-b2 version of the rt2570 driver. This works with kernels versions 2.6.16 and less. It compiles for 2.6.17 but I do not know how to configure the interface under this kernel, so I do not know if it works.
Yours is much higher. You'll need to look for an updated driver, or updated instructions.

---

### Post by devosion on 2007-11-02
Ah, that can be a problem. I should have read that a little more thoroughly. I'll look for another option then.

---

