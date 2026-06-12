---
title: "Success.. Configured/booted from Software Raid on ASUS AV8-E SE"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by dlafary on 2006-02-03
I finally got the raid 1 configured on my ASUS AV8-E SE motherboard with two Maxtor SATA 250 gb hard drives. It boots and loaded fine.
The trick was in the partitioning. I followed the procedure outlined by
[www.howtoforge.com/linux_software_raid](www.howtoforge.com/linux_software_raid). I was stumped when doing the partitioning. I created each partition as a primary. I needed to select the use as being Linux Raid. I did that for each partition. /boot, /swap. / , and var as outlined. Be sure to make the boot partition bootable on both drives by setting the boot flag on. I have not tested the raid as of yet to see if the system will continue with one drive out. But after seeing other people having trouble just trying to get it to work and boot, I feel that I have achieved something as a beginner.\\:D/

---

