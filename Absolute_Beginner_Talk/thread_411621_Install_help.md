---
title: "Install help"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by kineem on 2007-04-17
Hello. New to Ubuntu but glad to be here. I have a 80gb hard disk with only one partition on which W&#304;ndows installed. There is 50 gb free space now on that partition.  I dont want to destroy my windows install but to install the Ubuntu on the very 50 gb free space. Is such an install possible? If there is a guide it would be wonderful,too.
Thanks in advace.

---

### Post by Bachstelze on 2007-04-17
Yes, it is possible. Just use GParted to resize your Windows partitions.

Keep in mind, though, that nothing in this world is 100% safe so please make proper backups of all valuable data beforehand ! You'll probably never need tu use them but better being safe than sorry.

---

### Post by joeblow1102 on 2007-04-17
It also depends on what version of Windows you're running.  I would recommend getting the newest version of the gparted livecd and burning and booting into that.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by robenroute on 2007-04-17
Hi there,

Linux wants to be installed into a separate partition; just having free disk space is not sufficient. What you basically need to do is:

1.) clean up Windows (run the disk clean up, check disk and defrag disk tools in Windows)
2.) make the existing Windows partition smaller
3.) create a new partition (for Linux, using the ext3 file system format)
4.) install Linux to this new partition

Steps 2,3 and 4 are best done with a freely downloadable utility called GParted. Easiest would probably be to download the Live GParted version (check at distrowatch.com) and burn a bootable CD.

Just make sure you backup your Windows data/documents before resizing your Windows partition. Nothing will probably go wrong, but better safe than sorry ;-)

---

