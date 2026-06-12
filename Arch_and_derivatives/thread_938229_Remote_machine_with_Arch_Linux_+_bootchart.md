---
title: "Remote machine with Arch Linux + bootchart"
date: 2008-10-04
forum: Arch and derivatives
---

### Post by Calmatory on 2008-10-04
Well, my remote machine has Arch installed, and I was curious to see the bootchart image. However, after I installed bootchart, modified the menu.lst, nothing shows up after I do bootchart-render, except "/var/log/bootchart.tgz not found".


As the machine is remote, I can not check wheter or not does the machine boot with the right GRUB entry, though, using another entry for bootchartd does nothing different. :|

Here's part of the menu.lst:
```

# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 init=/sbin/bootchartd root=/dev/disk/by-uuid/0f6339f3-b826-4c83-b3c8-e8a60f33f915 ro
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/0f6339f3-b826-4c83-b3c8-e8a60f33f915 ro
initrd /kernel26-fallback.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1


```

Any ideas?

---

### Post by Barrucadu on 2008-10-04
Right, let's start with the completely basic questions first:
1) Did you reboot it?
2) Does GRUB boot the first entry by default?

---

### Post by Calmatory on 2008-10-04
I did reboot. It should boot with the first entry, though changing "init=/sbin/bootchartd" does nothing different.

---

