---
title: "resize partition"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Rita G. on 2007-04-27
i want to resize my partition /dev/sda2 to make it smaller BECAUSE IT'S TOO BIG and i could stick another OS in there. so i applied qtparted from synaptic package mgr. and launched it.....
it said:
“no device found. maybe you're not using root user?”
anybody know how to work this?

---

### Post by Najand on 2007-04-27
Open a terminal (console) and run:
```
 sudo qtparted

```

---

### Post by DSn0wMan on 2007-04-27
I am not sure about qtparted, but when I want to resize a partition I use the gparted live cd.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Najand on 2007-04-27
Gparted is also included in repositories. I think qtparted is also a similar thing for KDE.

---

### Post by psionyk on 2007-04-27
You cannot resize partitions while they are "mounted", which means that they are currently in use by your operating system when you're running it.  The best way would be to download and burn gparted live cd to a disk and boot into that.  By doing so, the partition you want to shrink will not be mounted and you can safely resize it.

Here's the site to download gparted:

[[COLOR="DarkRed"]_http://gparted.sourceforge.net/livecd.php_[/COLOR]]("http://gparted.sourceforge.net/livecd.php")

What OS is currently on the partition you want to shrink?

---

