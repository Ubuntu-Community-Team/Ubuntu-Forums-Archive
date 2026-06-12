---
title: "Low Disk Space"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by brenbart on 2006-06-26
I installed Dapper 6.06 on a compaq Presario 1200 XL118 with 192MB RAM but only a 2GB hard drive.  My drive is partitioned as follows:

FileSystem     Size     Used     Free    Use%    Mounted on
/dev/hda1     1.8G     1.7G     68M     97%     /
varrun           90M     84K      90M     1%      /var/run
varlock          90M     4.0K     90M     1%      /var/lock
varrun           90M     84K      90M     1%      /dev
varrun           90M     84K      90M     1%      /dev/shm
varrun           90M     84K      90M     1%      /lib/modules/2.6.15-25-386/voli
/dev/hdc       693M    693M    0         100%  /media/cdrom0

Naturally if I try to add any application or update the OS it fills the HD and tanks on reboot.  What are the minimum system applications needed to run?

Or what is something I can delete?  

Looking in the Synaptic Package Manager it doesn't look like any of the packages are really that large including Open Office which given my MS Office experience I expected to be mammoth.

I already tried running 'sudo apt-get clean' and 'sudo apt-get autoclean' which managed to get me 68M free and allowed me to log on but what is taking up all the space?

---

