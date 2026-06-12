---
title: "GRUB help"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by gitargr8 on 2006-12-30
Hello all, I just installed Ubuntu 6.10, and everything went fine, but I installed grub to the wrong boot partition. I have two hard drives, a 320 GB SATA drive that I want to boot off of, and a 120 GB IDE drive that grub was installed to.

The way I see it, I have three options: 

  1) change the Windows boot.ini to include Ubuntu

  2) install GRUB to the correct MBR

  3) reinstall Ubuntu

Obviously the easiest for me would be number 3, but that is time consuming and would much prefer 1 or 2. If anyone can help, I would greatly appreciate it.

~Ryan

---

### Post by mykalreborn on 2006-12-30
check out this post:[http://ubuntuforums.com/showthread.php?t=297548](http://ubuntuforums.com/showthread.php?t=297548)
hope it helps

---

### Post by pseudonym on 2006-12-30
Hi, [this thread]("http://ubuntuforums.org/showthread.php?t=24113") gives you 2 ways of carrying out your option 2. To be on the safe side, I would temporarily unhook your IDE drive, since GRUB likes to install itself there if it can (the root cause of your problem).

Is windows installed on that IDE drive? If so, you'll now need to boot up your windows install CD and go into the recovery console to restore the MBR (the CD tells you what to do).

Now boot into Ubuntu. Because windows wasn't present when you re-installed grub, you'll need to edit /boot/grub/menu.lst manually to include it. In a console type - ```
sudo nano /boot/grub/menu.lst
``` and follow this example - ```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Wintendo (you can name it how you like :) )
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Save and exit nano. You should now be able to boot happily between your OSes. :)

---

