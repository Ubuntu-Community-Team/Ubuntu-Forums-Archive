---
title: "permission denied"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by buccaneere on 2007-11-24
/etc/initramfs-tools/conf.d/resume

That was the command, after updating, and the return was 'permission denied'.

What do I do here???

---

### Post by AndyCooll on 2007-11-24
```
sudo /etc/initramfs-tools/conf.d/resume
```

That should do the trick.

Beyond your home directory you usually need admin rights to activate or modify files.

:cool:

---

### Post by buccaneere on 2007-11-24
> **AndyCooll said:**
> ```
sudo /etc/initramfs-tools/conf.d/resume
```

That should do the trick.

Beyond your home directory you usually need admin rights to activate or modify files.

:cool:

Good call.

I just did auto conversions for boot/grub/menu, and etc/fstab, as sudo. Maybe try it again - same mode? DUH!

Thanks

---

