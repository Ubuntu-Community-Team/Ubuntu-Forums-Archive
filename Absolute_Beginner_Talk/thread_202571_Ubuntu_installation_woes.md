---
title: "Ubuntu installation woes"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by SaferSephiroth on 2006-06-23
Hey guys, i got a new laptop and decided to install Ubuntu. I explored the live cd for a few days and liked it, so i decided to install. I already have windows on it and made windows set a ~20GB unallocated partition that Ubuntu recognises. I made Ubuntu "install on continuous free space". However, after the installation from the live cd was over, my problems began.

The system rebooted (live cd was removed prior) and i picked Ubuntu (not recovery) from the dual boot screen. Then the system got hung on 'Mounting root filesystem'. It tries to find it for a while, then i get a command line with the following errors:

ALERT! /dev/sda2 does not exist. Dropping to a shell!

/bin/sh: can't access tty; job control turned off


Any suggestions?

Thanks.

---

### Post by aysiu on 2006-06-23
Maybe [this](http://www.ubuntuforums.org/showthread.php?t=188376) might help...? Maybe not.

---

### Post by SaferSephiroth on 2006-06-23
My laptop is an asus, however, it didn't work. I waited for nearly 5 min and booted again. Any other suggestions?

---

### Post by catlett on 2006-06-23
Can you boot into windows? If so install the ext 2 driver so you can see your Ubuntu partition. Get it here [http://www.fs-driver.org/](http://www.fs-driver.org/) Go to "My Computer" and double click the hard drive icon to open up the ubuntu partition in explorer. The partition should have similar folders to the screenshot I posted.

If it doesn't appear correct I would reinstall. BUT I would use Gparted Live to make my partitions first. Get it here [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) Clear any partitions you have other than windows. 

Make 2 partitions. 1 for swap (this is virtual memory like window's swap file) This should be formatted to "linux-swap" and it's size should be  twice your ram i.e. 256mbv ram = 512mb swap. Make another partition for the install. 20gb or whatever. Format it to ext3.

Rerun the installation and choose "manualy edit" the partition table. This will lists your partitions and have drop down menu boxes in front of each. In front of your 512mb swap choose "swap" from the drop down menu. In front of your 20gb partition choose "/" from the menu. ( / is the label for root)

Your other partition (windows and any other partition you may have) leave alone. Keep the setup and label the way it is. The installer will mount it for you.

Make sure you DOI NOT check off the circle with the heading "format?" after your windows partition. That will (of course) erase any data. The / and swap doesn't matter. Let the installer default to what it wants.  If it doesn't format that is O.K. because you already did. If it does format that is O.K. too because there is no data on the partitions.

Let the installer run to the end.Hopefully this will be the end of it. If not you might want to use the Alternate Install Cd. It allows you to control the configuration more than the Live Cd. You can download it here [http://www.ubuntu.com/download](http://www.ubuntu.com/download) at the download site. Just scroll down after you choose a mirror past the Desktop CD and the Server CD until you get to the Alternate Install CD.

Either one you choose, there is a link for a how to in my signature just in case you want them.

---

