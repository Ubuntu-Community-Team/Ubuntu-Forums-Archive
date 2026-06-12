---
title: "Ubuntu cannot load from partition"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by xItachi on 2008-02-23
Hi, before my problem I was dual booting Vista and Ubuntu.  I formatted my Vista partition and installed Windows XP and I also removed a partition called DellRestore which is a Dell recovery partition.  After I removed this, I think my Ubuntu partition number got bumped up from 3 to 2?  I can't boot from grub anymore, it says cannot read from partition or something like that.  I booted from the LiveCD and did 

```
find /boot/grub/stage1
```

it returned (hd0,2) <--- before it was always (hd0,3)

then i did 

```

root (hd0,2)
setup (hd0,2)

```

That was successful but it still does not load from the partition.  By the way I am not very sure what the root and setup commands actually do, I read those commands online and always did those commands to fix the bootloader every time I resize the partitions.  Does anyone know what I should do?  Thanks

---

### Post by dcstar on 2008-02-23
> **xItachi said:**
> Hi, before my problem I was dual booting Vista and Ubuntu.  I formatted my Vista partition and installed Windows XP and I also removed a partition called DellRestore which is a Dell recovery partition.  After I removed this, I think my Ubuntu partition number got bumped up from 3 to 2?  I can't boot from grub anymore, it says cannot read from partition or something like that.  I booted from the LiveCD and did 

```
find /boot/grub/stage1
```

it returned (hd0,2) <--- before it was always (hd0,3)

then i did 

```

root (hd0,2)
setup (hd0,2)

```

That was successful but it still does not load from the partition.  By the way I am not very sure what the root and setup commands actually do, I read those commands online and always did those commands to fix the bootloader every time I resize the partitions.  Does anyone know what I should do?  Thanks

```
setup (hd0)
```

---

### Post by xItachi on 2008-02-23
That doesn't work.. I checked again and it says Error 22: No Such Partition.

---

### Post by xItachi on 2008-02-23
I think my /boot/grub/menu.lst is pointing to (hd0,3) to try to boot when it has actually been moved to (hd0,2),  How do I change this?

---

### Post by xItachi on 2008-02-23
Okay, I solved it.  For those of you who want to know:  When you get to your Linux Bootloader, press 'ESC' key and press 'e' to edit the boot parameters.  On the top it says 'root (hd0,3)' which was my old partition, press 'o' to add a line under it and 'e' to edit the parameter, then type 'root (hd0,2)' which is my new partition number.  Press 'b' to boot and then you can edit /boot/grub/menu.lst and fix it

---

