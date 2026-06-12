---
title: "Skip Checking Fat32 Partitions at Boot?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by LaneLester on 2006-12-12
During the boot process, all of the partitions are checked... and I have a bunch of them, making boot a lengthy process. Particularly pokey are my several fat32 partitions. For each one there is a complaint about a discrepancy between two somethings and the statement that nothing is being done about it.

My fat32 partitions are just fine, and I would like for Ubuntu to quit checking them. Is this possible?

Lane

---

### Post by bodhi.zazen on 2006-12-12
> **LaneLester said:**
> During the boot process, all of the partitions are checked... and I have a bunch of them, making boot a lengthy process. Particularly pokey are my several fat32 partitions. For each one there is a complaint about a discrepancy between two somethings and the statement that nothing is being done about it.

My fat32 partitions are just fine, and I would like for Ubuntu to quit checking them. Is this possible?

Lane

Yes. Edit fstab.

Open the editor of choice as root:```
gksudo gedit /etc/fstab
```

change the last digit to a zero:
> /dev/hdxy /mount/point vfat options 0 **[color=darkred]0[/color]**

---

### Post by LaneLester on 2006-12-13
Thank you very much for your help.

Lane

---

