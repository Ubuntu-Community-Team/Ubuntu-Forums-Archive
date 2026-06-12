---
title: "HFS+ Support On Boot"
date: 2010-09-27
forum: Apple Hardware Users
---

### Post by majasticmoose on 2010-09-27
I was wondering if one could mount HFS+ partitions during booting (initramfs) with ubuntu NOT installed. 

I have almost finished making Wubi for mac (Mubi) but ubuntu doesn't install because it can't mount the HFS+ partition (where the ISO is).

How would I do this?
Thanks,
Andrew

---

### Post by srs5694 on 2010-09-27
Can you compile a custom kernel? If so, you might get it to work by compiling HFS+ support directly into the kernel, rather than as a module. You could also look at the /etc/initramfs-tools/modules file, which specifies modules that are to be loaded from the initial RAM disk when it boots.

---

### Post by majasticmoose on 2010-09-27
Ok. Kernel has the module here /lib/modules/$(uname -r)/kernel/fs/hfsplus/hfsplus.ko 

How do I get that in initramfs?

---

