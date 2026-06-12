---
title: "Freebsd direct boot not working"
date: 2013-04-23
forum: Any Other OS
---

### Post by tangi on 2013-04-23
Hi,

Can you please help me on this issue.
I'm getting this error message when trying to load FreebSD 9.1 i386 kernel using grub v1.98.

```
grub> kfreebsd /boot/kernel/kernel
error: address 0x65000 is out of range.
```

That works on amd64 version. Don't understand why not on i386.

Thanks

---

### Post by tgalati4 on 2013-04-23
Why can't you use a 64-bit version for freebsd?  It looks like a 32-bit vs 64-bit issue.  Perhaps use the chainload +1 for that partition to load freebsd.  That would at least keep the bootstrap in 32-bit mode for the kernel to load.

Perhaps use grub-probe to get more information on what it thinks is on that partition.

```
man grub-probe
```

---

