---
title: "Grsync Very Slow After Freshinstall"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by ityro on 2007-08-05
Hello All,

I recently completed a Fresh Install after crashing my system. My original Fresh Install was Dapper followed by Upgrades to Edgy and Feisty with no problems.

When I did my first backups after this fresh Install I was surprised at how slow grsync was.  Before the freshinstall my grsync system backup took about the same time as my tar system backup, 15-20 minutes.

I just completed both backups to my external HDD and the tar backup (compressed, tgz) took 13 minutes and the backup file size is 963MB, while the grsync backup (not compressed), took 98 minutes and the backup size is 2.3GB  with a transfer rate of 419,815 B/s.(I changed the source from "/" to "//" and it ran in 85 minutes).

Considering the compression on the tar file 2.3GB for the grsync backup looks good, df -Th indicates 3.0GB used in the system partition.

To make it more interesting grsync produced this message three times out of 6: "Warning: Files disappear so quick not transferred". I simply ran the job again which only took a minute and produced no warnings.

I have verified all dependencies and reinstalled both rsync and grsync. 

My questions if anyone has an opinion:

1. Why is grsync taking so long to run now, or should the question be how did it run so fast prior to my last fresh install?
2. Should I be concerned about the warning message?

If anyone has an idea of what has changed or a path for me to follow I would like to hear from you.  My search of the forums produced nothing I recognized as helpful. 

My tar job is:  "sudo tar cvpzf /media/usbdisk/tar-back.tgz --exclude-from=exclude.lst /".  The screen shots show my grsync settings and the exclude list used by both my tar and grsync jobs.

Thanks for your time.


MY SYSTEM: Dual-boot XP/Ubuntu 7.04 on a HP/Compaq nx9010 (Pentium 4-2.66GHz) notebook w/768MB RAM, 40GB HDD and an Iomega 80GB usb HDD. ATI Display: PCI Bridge [GP 340M] Radeon IGP 330M/340M/350M.

---

### Post by ityro on 2007-08-05
Here we go again:

---

