---
title: "installing 320GB ntfs drive"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by speed32219 on 2007-02-23
I have set up a Ubuntu 6.1 media server (466Mhz with 192MB sdram) with a Xbmc media center.  I had isntalled a 250GB HD formatted using ext3 and copied 49 dvd's and thumbnails (ISO) from my XP machine using the LAN at 100 Mbps.  Need less to say it took a long time.  I installed a DVD drive in the Ubuntu box and tried to convert my DVD's to ISO format but it took a very long time due to processor power and mem limitatioins.  

So what I would like to do is isntall the new 320 GB in XP and do my conversions (VOB to ISO) there and just install the drive into the Ubuntu media server when finsiished.  Of course it would be formatted in ntfs.  Now I read where I can install ntfs-3g with Ubuntu and it will be able to mount, read/write to this new drive. (Once loaded there will be no space to write, but you never know when I may want to remove a movie/s and add something different)

Would this be the fatest way to accomplish this?

Or should I do all the ripping on my XP machine and just continue to transfer the ISO's accross the LAN to the 320GB ext3 formated drive.  (Takes about 20 min. per 4.35GB dvd)

---

### Post by SeanTater on 2007-02-23
I don't have any guarantees, but I imagine it would take just as long or longer to wipe your drive and format ntfs, so how about trying the Windows ext3 driver:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

