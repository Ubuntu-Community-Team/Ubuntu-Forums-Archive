---
title: "Black screen after 12.10 install"
date: 2012-11-19
forum: Apple Hardware Users
---

### Post by rlinsurf on 2012-11-19
I've taken the following procedures. In Mac OS X, use Disk Utility to create a single Free Space partition on my second HD. Install rEFIt. Restart a couple of times to make sure rEFIt is loading. Boot from the Live CD, use gparted to create a new partition scheme, a Linux-swap if 1gb, and a EXT 4 mapped to / of about 2tb. Install the boot loader to the EXT 4 partition. Install. 

Reboot. rEFIt comes up and I used Partition Manager. rEFIt reported the partitions were already in sync, so need to sync them. I then chose the Ubuntu HD to boot from. 

It shows the rEFIt Linux penguin symbol and just sits. It's now been about 20 min.

---

### Post by rlinsurf on 2012-11-19
A bit more progress. I rebooted again, and this time was able to access the grub menu by holding down the shift key just as the screen went black. The instructions I read said to change to nomodeset, but no such menu appears. All I get is Ubuntu, Ubuntu in recovery mode, and other options having to do with Mac OSX. I chose recovery mode, and again, there's no option for nomodeset. I try the failsafe for graphics recovery, then return when Yes is highlighted. 

Then it just sits there at a screen which reads:

"Continuing will remount your / filesystem in read/write mode and mount any other filesystem defined in etc/fstab. Do you wish to continue." 

Yes is highlighted. After pressing enter, the screen remains, but below is displayed:

"fsck from util-linux 2.20.1
dev/sdb2: clean" and a line of data. 

It then just sits there with a blinking cursor.  

I then tried control-command-F1 to try to get a terminal. I got a grub prompt, but no command I entered was found, including all the ones listed it would recognize, much less sudo or apt-get. 

Anyone know how to get nomodeset during the first boot? Or how to enter terminal commands?

---

