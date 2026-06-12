---
title: "How to uninstall Linux?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by rbsis on 2007-07-22
How do I uninstall Linux Ubuntu? I am dual booting Windows XP Pro and Linux Ubuntu, I want to get rid of Linux because I don't use it and it is taking up a lot of space.

---

### Post by sad_iq on 2007-07-22
Get GpartedLive Cd...boot it...erase all linux partitions, create a new ntfs partition so you can use it with Windows...then insert your Windows disk boot into recovery console and type **fixmbr** (or something similar...you have to do this because when you remove linux your mbr will still contains grub, and will give errors and halt)
 Get Gparted Live Cd from here:[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by steve.horsley on 2007-07-22
I advise foing that in the other order. First replace the GRUB bootloader with the windows bootloader so it boots straight into windows. Then you can delete the linux partitions safely, and won't be left with an unbootable PC.

---

