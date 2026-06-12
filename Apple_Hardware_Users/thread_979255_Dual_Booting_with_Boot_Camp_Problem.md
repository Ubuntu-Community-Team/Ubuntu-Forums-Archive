---
title: "Dual Booting with Boot Camp Problem"
date: 2008-11-11
forum: Apple Hardware Users
---

### Post by dinovo.phil on 2008-11-11
Hey everybody. As suggested by the title, I'm trying to get my Macbook Pro to dual boot both Mac OS X and Ubuntu using the Boot Camp software bundled with Mac OS X. I followed the instructions here: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) (the 'Ubuntu and Mac OS X (Dual Boot, no rEFIT)' section) but when I hold option while booting up, the only drive it lets me choose to boot from is HDD. Basically, although everything was apparently installed fully, it doesn't recognize that there is a bootable linux partition.

AN IMPORTANT NOTE:

When I ran the install process from the Ubuntu 8.10 LiveCD, I got to the section of the install where you are just about to press the actual install button, but before doing so I went into advanced options and deselected the "Install Ubuntu Bootloader" checkbox for fears it would override the native Mac OS X bootloader. If this is why it isn't working, can someone reassure me that it will not interfere with the whole "hold option for boot menu" system already set up?

---

### Post by Tu1J4kXk8NUhMz on 2008-11-11
Three thoughts/questions/ideas:

1. Is there any reason you don't want to use rEFIt? I don't want to say "just use rEFIt" because you could have your reasons. It would simplify things, but it's probably not necessary.

2. In reading the guide link you provided, it never really says to delete the NTFS partition that Boot Camp creates. I apologize if this sounds to basic, but did you delete that and recreate it as an ext2/3 (whichever you prefer)?

3. The boot loader is actually kind of important. From what I can tell, it's what Boot Camp/rEFIt uses to identify a Linux operating system. So that may be the problem. If at all possible, reinstall and make sure you inject the boot loader into the partition you install Ubuntu to. No, it doesn't effect Boot Camp...if anything, it helps! I'm sure there are ways to install GRUB (the ubuntu boot loader) without a complete reinstall, but off the top of my head I don't know them.

4. You issue may be, in fact, a problem with Boot Camp. Not that something's wrong or corrupt with it. From my experience, the Boot Camp loader doesn't play well with Ubuntu for the reason I stated before. I THINK (I'm not totally sure) that the Boot Camp Loader looks for Windows in the second partition. If it doesn't find it, it doesn't work. 

Please let me know how everything above effects you. Hopefully I can help you from there.

---

### Post by cyberdork33 on 2008-11-12
There is a bug in the installer. Please check the FAQ at the top of the forum.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

