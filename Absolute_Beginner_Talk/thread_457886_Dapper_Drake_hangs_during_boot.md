---
title: "Dapper Drake hangs during boot"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by edgarpole on 2007-05-29
I have installed Xubuntu 6.06.1 on my Dell Latitude laptop CPi R400GT (6GB hd and 196MB RAM). All went well at first but now when I boot it always hangs when "loading hardware drivers" . I do not have another OS system on the hard disk. I have re-installed several times using both the desktop cd and the alternate version but there has been no improvement. Now it even hangs at the same place when I try to re-install. I also tried 7.04 Feisty Fawn but there appears to be a bug when the hard disk is partitioned which I do not have the technical expertise to work around.  Any advice would be greatly appreciated

---

### Post by sankarv on 2007-05-29
problem may be with the hard disk sectors. have you formatted your hard disk properly? backup any data if needed and then erase the entire hard disk. This will even delete entire system partition table so that you can freshly install it again. this should work since u say it has booted before. also choose the file system such as ext3/reiser fs. ext2 is not stable. use the desktop version as it will be easy one.

---

### Post by overdrank on 2007-05-29
> **edgarpole said:**
> I have installed Xubuntu 6.06.1 on my Dell Latitude laptop CPi R400GT (6GB hd and 196MB RAM). All went well at first but now when I boot it always hangs when "loading hardware drivers" . I do not have another OS system on the hard disk. I have re-installed several times using both the desktop cd and the alternate version but there has been no improvement. Now it even hangs at the same place when I try to re-install. I also tried 7.04 Feisty Fawn but there appears to be a bug when the hard disk is partitioned which I do not have the technical expertise to work around.  Any advice would be greatly appreciated

HI, I just install ubuntu on my son's dell last night and finally had to use the alternate cd. You might check in bios to see how much ram is allocated to you video. You might be able to  adjust the amount used for video to a lower setting which will allow the installation. And if you will create the swap partition first this will allow the system to use it for memory during the install. Hope this is not to technical and it helps.Good luck!:)

---

### Post by edgarpole on 2007-05-29
Hi

Thanks for the advice. I have tried all suggested but still no go. I re-formatted the hard drive and tried to install 6.06.1 but still hung at "loading hardware drivers" Checked BIOS only 4 MB used for video so I think I will reinstall XP  and try to live with it!

Thanks again

---

