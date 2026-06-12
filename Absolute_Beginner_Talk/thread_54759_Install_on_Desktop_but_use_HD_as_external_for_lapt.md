---
title: "Install on Desktop but use HD as external for laptop"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by Rapaport on 2005-08-05
I'm wondering if anyone has tried installing Linux on a desktop with only 1 hard drive (hd0) and then removed that hard drive and tried to boot linux off the hard drive as an external hard drive on a notebook that supports USB booting in BIOS.

I've run into all kinds of problems installing Linux from my notebook to an external and I'm looking for other options. I can't seem to get my distro (Ubuntu) to boot off the USB drive.

The error I have received each time I install on the external USB HD (40GB) is
```

pivot_root: no such file or dir
/sbin/init:428 cannot open dev/console no such file
Kernel panic - not syncing attemtped to kill init
```

Anyway, please let me know if anyone has tried the above (installing on desktop and then using that desktop HD as an external HD) as I am desperate for a stable Linux install on my external HD so I can begin to learn about Linux.

---

### Post by xmastree on 2005-08-05
[QUOTE=Rapaport]I'm wondering if anyone has tried installing Linux on a desktop with only 1 hard drive (hd0) and then removed that hard drive and tried to boot linux off the hard drive as an external hard drive on a notebook that supports USB booting in BIOS.

I've run into all kinds of problems installing Linux from my notebook to an external and I'm looking for other options. I can't seem to get my distro (Ubuntu) to boot off the USB drive.

The error I have received each time I install on the external USB HD (40GB) is
```

pivot_root: no such file or dir
/sbin/init:428 cannot open dev/console no such file
Kernel panic - not syncing attemtped to kill init
```

Anyway, please let me know if anyone has tried the above (installing on desktop and then using that desktop HD as an external HD) as I am desperate for a stable Linux install on my external HD so I can begin to learn about Linux.[/QUOTE]
 All I can think of is that the boot loader is trying to boot from /dev/hda but when the drive is in the USB slot, it's no longer /dev/hda but something else...

---

