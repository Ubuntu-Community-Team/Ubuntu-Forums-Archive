---
title: "Partitioning"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by skullkid on 2008-01-08
I hate partitioning... :( I keep getting that "mounting" error that youre supposed to go to Removable Drives and Media and stop the drives from being mounted automatically after I try to resize. I unchecked the two check option things that say "Mount removable drives when hot-plugged" and "Mount removable media when inserted." (I hope those are the right ones. If they arent, inform me please) but I still get the error.

---

### Post by kpkeerthi on 2008-01-08
Yes... that should work. Not sure why it keeps mounting the drive. You can try to partition with cfdisk from Live CD. cfdisk is semi-graphical (think ncurses). I assume Ubuntu Live CD has it.

**Method - 1:**
1. First make sure the drive is unmounted.
```

umount /dev/<your-disk>

```

2. Open a terminal and type **cfdisk**. If you are NOT comfortable with cfdisk, try the options below.

**Method - 2:** (Preferred, as they are more up-to-date than Ubuntu Live CD)
You may want to use [GParted live CD]("http://gparted.sourceforge.net/livecd.php") or [System Rescue CD]("http://www.sysresccd.org/")

---

