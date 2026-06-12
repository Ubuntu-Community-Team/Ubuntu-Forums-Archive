---
title: "design engineer student"
date: 2008-11-12
forum: Apple Hardware Users
---

### Post by vijay.iyer12@gmail.com on 2008-11-12
hi all,

i'am currently an student. since m tired of win so i thought of trying my hands in a different OS.. so i opted for macbook white... beacues of its class and good performance and relaiability... but on the other hand since my study requires.. chip designings and all.. which i cant install in OSX.. but all these softwares supports win OS and Linux OS(32 bit and 64 bit respectively)......

so, initially i thought of installing both and making my system triple boot.. but now i changed my mind coz i ddont wanna make it run slow for no reason.. as i can very well do all my designing work in linux so no point instaling win.. since m not a gaming freak so i just dont want win...


so at this note i need some help regarding installing linux in my macbook so that i can do my designing work seperatly and for the rest of my work OSX is there....

i will be very grateful if anybody clarifies this doubt to me that how to install linux its pros and cons.. and everything and how to get a linux OS from net.....


thanks a lot

-Vijay-

---

### Post by PartisanEntity on 2008-11-12
From my experience:

Boot your mac from your mac installation cd

Create a new partition from the available free space you have

Then boot your computer from the Ubuntu LiveCD and install Ubuntu, when you get to the partitioner, select 'manual' and delete the partition you made using your mac install cd. Create a large ext2 or ext3 partition for Ubuntu and a smaller one, at least the same size as your ram for Linux Swap, then continue with the installation.

(From my experience, the partitioner on the Ubuntu LiveCD has trouble with hfs+ partitions, hence using the mac install cd as a first step to create a 'pre-partition' of sorts)

Hope this helps.

---

### Post by cyberdork33 on 2008-11-12
as a shortcut that I often suggest.

After creating your "pre-partition" with DiskUtility, boot the Ubuntu LiveCD and start gparted (partition editor) from the system > administration menu.

Delete the partition you made with Disk Utility and Apply Changes then exit. Then start the Ubuntu installer and choose to install to the "largest free space" and the installer will create the new root and swap partitions for you.

---

