---
title: "A Quick Question That's Probably Been Asked Before..."
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-07-18
Is there a way to make a back-up of Ubuntu, so I can resize the partition and not destroy anything?

---

### Post by shearn89 on 2007-07-18
you can set up a different /home partition, so all the settings are kept (or most of them). I also think its possible to increase the size of the partition without losing data?

---

### Post by tcoffeep on 2007-07-18
It's actually decreasing the size, and my HD is being 100% used by Ubuntu...I resized it in the past, and it refused to run for me....:( any ideas

[edit] not exactly 100%, there's a 2.5 gb swap partition.

---

### Post by shearn89 on 2007-07-18
Short of copying everything to a portable HD, i'm not sure you can do anything else...

---

### Post by Cappy on 2007-07-18
Gparted can do it with its hands behind its back:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Picture:
[http://gparted.sourceforge.net/screens/gparted_10_big.jpg](http://gparted.sourceforge.net/screens/gparted_10_big.jpg)

You can also use the Ubuntu Live CD and Gparted on it if your linux file systems are EXT2 or EXT3.

---

### Post by tcoffeep on 2007-07-18
That's what I used to resize my partition. I want to bring it down from 110gb to 85gb, but I'm scared that it's going to be a jerk off again (by jerk off, I'm speaking of gparted)

---

### Post by Cappy on 2007-07-18
You'll need to keep Ubuntu as the first partition on the disk so that GRUB can start. You can also leave a small 50MB partition as the front partition instead (that's what I did).
It's also possible you may need to reload GRUB afterwards:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

