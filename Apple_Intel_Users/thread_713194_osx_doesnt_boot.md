---
title: "osx doesnt boot"
date: 2008-03-02
forum: Apple Intel Users
---

### Post by kumkumji on 2008-03-02
after installing ubuntu on my macbook it doesnt read the mac system any more , even when i restart it goes to grub and the "c" does not work , is there away to boot from osx cd??

---

### Post by ronocdh on 2008-03-02
You absolutely can boot up from the OS X CD. This will enable you to look at your partitions and see whether the OS X installation is still there (and thus salvageable) or whether you accidentally installed on your entire hard drive, thereby effectively erasing OS X.

Also, I believe **sudo fdisk -l** should show you other partitions. If you only see Ubuntu, that might be an indication that OS X is gone.

---

### Post by cyberdork33 on 2008-03-02
should use parted to get the GPT version of the partition table:
```
sudo parted /dev/sda print
```

if you hold c at bootup you should boot from the cd. you can also hold Option and get a selection list of bootable items.

---

