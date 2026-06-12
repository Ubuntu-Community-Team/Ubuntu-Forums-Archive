---
title: "CD/DVDROM Hardware Acceleration"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2005-11-28
Anyone know how to enable optical drive hardware acceleration?  I always get a message with LinuxNero that I do not have it enabled.  Thx in advance.

---

### Post by flange on 2005-11-28
[QUOTE=echo $USER]Anyone know how to enable optical drive hardware acceleration?  I always get a message with LinuxNero that I do not have it enabled.  Thx in advance.[/QUOTE]

I assume you mean enabling DMA?  If that's the case, then you need to open a terminal and type...

```
sudo hdparm -d1 /dev/hdX
```

where 'X' is the drive letter for your hard drive and/or cdrom.  My hard drive is '/dev/hda', and my cdrom is '/dev/hdc' (also '/dev/cdrom').  You can find out the drive letters for your comptuer by typing...

```
cat /etc/fstab
```

in a terminal window.

Hope that helps.

---

