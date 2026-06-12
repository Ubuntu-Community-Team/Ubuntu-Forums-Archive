---
title: "Display issues after waking from suspend. Fresh install of Xubuntu. Radeon hd 2600"
date: 2017-01-24
forum: Apple Hardware Users
---

### Post by skeetwood-mac on 2017-01-24
I just installed a fresh install of Xubuntu on my older iMac. I had Elementary OS on it before with no issues. Everything seemed to go well and once I started using the restricted driver for the wireless card everything seemed to be working fine. Then the first time I put it to suspend I realized it was not ok. See attached image. This is how it returns from suspend. Nothing seems to fix it other than a full reboot. I'm assuming this is a driver issue but I'm not sure how to go about trying to fix it. Is it possible it could be something else? There were no restricted drivers listed for the video card so I'm not sure what to do. The card is a Radeon hd2600.

Thanks in advance!

---

### Post by howefield on 2017-01-24
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by 6-john-u on 2017-02-07
Exact same issue here. Also occurs in Fedora.

---

### Post by 6-john-u on 2017-02-09
For anyone experiencing this issue, I found a work around.

The issue only happens when booting up via EFI. So, in order to install Ubuntu in legacy/bios/csm mode: boot up from the install media, run gparted, wipe the disk, create a new MBR/MSDOS partition table, and setup the partitions as required (I created three partitions, 60gb for root, 4gb for swap, and the rest for home - the actual mount points are configured later, during installation). At this point, you can run the Ubuntu installer normally and tell the installer to use the partition structure you created via the "Something else" disk option.

This fixed the issue for me.

Good luck.

---

