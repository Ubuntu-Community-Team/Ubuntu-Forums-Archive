---
title: "Does a kernel change mean recompiling  driver"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-02-15
Through automatic updates the default kernel is now 2.6.17-11-386
This has caused my Intel536 faxmodem driver to be no longer present. I tried copying the absent driver intel536.ko to the lib/modules/kernel/drivers/char directory of this particular kernel from the previous one, but this doesn't work.  It doesn't work, the modem cannot be found. Will this driver not work because it wasn't compiled in this kernel or is there another explanation?

---

### Post by renzokuken on 2007-02-15
new kernels usually mean you have to reinstall any drivers you installed on a previous kernel

if you copied the .ko file across though, you could try loading the module manually

```
sudo modprobe intel536
```

---

### Post by luvinit on 2007-02-15
It gives me the fatal error thingy. Thanks, I will try sometime, in the meantime I will use the easy option and boot into the old kernel.

---

