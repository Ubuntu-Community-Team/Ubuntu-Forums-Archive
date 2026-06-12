---
title: "Bootloaders (yaboot specificaly)"
date: 2005-10-31
forum: Apple PPC Users
---

### Post by leverknight1 on 2005-10-31
has anyone used this? and if so here is the situation i have an imac bondiblue and i installed 9.2.2 and when i did hat i parted the hard drive to a 2gig mac and a 2 gig linuxppc prefered format that was working fine but when i installed os X after that i installed fedora core 4 and it was still working fine.

So like 2 months later i needed to update some software off cd and yaboot didnt want to boot the cd and so i just held the "c" key right booted fine got it installed didnt use it til like 2 hours ago and i cant get into the bootloader i dont want to format the drive less it is the only option my gf spent 3 hours making here background image on it.

all i want to do is to boot into fedora core and copy that file to my other linux box and format the entire drive in my imac and run just a single os or just net boot it.

---

### Post by jdp on 2005-11-02
[https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot)

The last section can help you get the files off the partition or reinstall yaboot.  Forcing it to boot with something other than yaboot can wipe yaboot from the OF.  

The easiest solution in the future is to partition with empty space for Linux at the start of the drive and make the MacOS partition as the second.  In OS X Disk Utility you set it for two partitions, size them as you like, but then set the first for "Free Space" or "Unallocated Space"

I'm not sure if the 8,4GB limit applies to yaboot, or just booting straight from OF on the old iMacs.

---

### Post by lorne_kun on 2005-11-04
Hello guys, just discovered ubuntu for PPC and I have a few questions about dual booting Tiger 10.4.3 with ubuntu 5.04 (or 5.10 for that matter). I really like the way this runs on my powerbook, but I cant fully abandon my Tiger yet ;). Is there a tutorial about dual booting on the site somewhere?

---

### Post by leverknight1 on 2005-11-12
[QUOTE=lorne_kun]Hello guys, just discovered ubuntu for PPC and I have a few questions about dual booting Tiger 10.4.3 with ubuntu 5.04 (or 5.10 for that matter). I really like the way this runs on my powerbook, but I cant fully abandon my Tiger yet ;). Is there a tutorial about dual booting on the site somewhere?[/QUOTE]

do you have the install cd for both 10 and ubuntu?
if so all you do is backup all your files that you want to save from os 10. Then put in the ubuntu cd and when the partioner starts up edit your partion table manualy, and delete all partions that are there then create 2 new ones of equal space and install ubuntu on the one closest to the top so that your bootloader is first, and then you can select whatever os you want of the list.  After that you should be able to install os x normally when you finish installing ubuntu.  You have to make sure you dont select the format harddrive part in the os 10 installer if there is one i havent been able to get my hands on a machine able to run 10.4 until xmas when i get a mini.

---

