---
title: "Ubuntu on a Macbook Pro"
date: 2008-11-19
forum: Apple Hardware Users
---

### Post by oceanfirehawk on 2008-11-19
I have a Macbook Pro 2.4 Core 2 Duo and I would like to install Ubuntu on it.

I followed [https://help.ubuntu.com/community/MacBookPro#Ubuntu%20and%20OS%20X%20(Dual%20Boot,%20no%20rEFIt](https://help.ubuntu.com/community/MacBookPro#Ubuntu%20and%20OS%20X%20(Dual%20Boot,%20no%20rEFIt))

but it was hard to understand near the end and it did not work. 

Does anyone have a surefire instruction on how to do it without rEFIT?

---

### Post by cyberdork33 on 2008-11-19
you need to use refit due to a bug in the Ubuntu installer. You can remove it afterward if you like. See this post:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

Here is my standard "easy install" method:

[LIST=1]
[*]Install rEFIt first anmd make sure it is working (you should get a boot chooser on startup...)
[*]Use Bootcamp or DiskUtility to create a partition at the end of the disc. Don't worry about what format, just make it the size you want for Ubuntu and your swap partition.
[*]After that boot the Ubuntu LiveCD and start the partition editor (gparted) under System > Adminstration. Use gparted to delete the partition you just made in OSX. It should be the last partition on the disc and follows after the HFS+ partition (OSX). Deleting it will leave free space. Apply changes and exit.
[*]Start the Ubuntu Installer from the desktop icon. When prompted, choose to install to the "largest continuous free space". This will let the installer create a root partition and a swap partition in the free space you made. On the last dialog of the installer, be sure to click the  "Advanced" button and choose to install grub to /dev/sda3.
[*]Reboot when done with the install, and in the rEFIt menu, choose the partition tool. It will attempt to sync the partition tables on your disk. Then SHUTDOWN the computer (not reboot), and start it up. You should be able to boot to Ubuntu now. If it seems to freeze on the tux logo, completely shutdown again and try one more time.
[*]Once you have everything working, you can uninstall refit as instructed on their website: [http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)
[/LIST]

---

### Post by MGump on 2008-11-28
This works brilliantly! It is far better than the WIKI help article for installing Ubuntu on a Macbook Pro.

If you follow the instructions above EXACTLY, you will have a perfect dual booting Macbook Pro that works in refit AND without (if you hold down OPTION while booting).

Thank you so much!

---

