---
title: "Clean Install Fear"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-11-15
Hi
I'm currently using a dual boot with Ubuntu 7.10 and XP. This was an upgrade from 7.04 to 7.10. 
I recently received the 7.10 CD from Canonical and I tried a clean install but whatever I did, it gave me a lot of problems. It mucked up my MBR, and wouldn't load XP. I had resolution problems and couldn't get internet access with Ubuntu so I had to go back to scratch reinstalling XP and then installing 7.04 before upgrading again.
I did read about using fixmbr from the XP disc but when I tried that, I didn't get any options about fixmbr. I got the options of Install XP, repair a partition or exit.
What I want to know is what is the safest way to do a clean install of 7.10 given the above. I have two hard drives with each OS having its own. 
Any advice or direction to suitable sites would be much appreciated.

Gazzadtfan

---

### Post by mikewhatever on 2007-11-15
By safest, do you mean MBR wise or performance wise (resolution, internet)? There are easy ways to fix mbrs, such as bootdisk or super grub disk.

---

### Post by SpiritIsReality on 2007-11-15
repair i think, but I don't know exactly. It's been a while since I've messed with the fixmbr. 

3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)

---

### Post by SpiritIsReality on 2007-11-15
> **mikewhatever said:**
> By safest, do you mean MBR wise or performance wise (resolution, internet)? There are easy ways to fix mbrs, such as bootdisk or super grub disk.

> The only thing we have to fear is fear itself.


[http://www.google.ca/search?hl=en&q=the+only+thing+we+have+to+fear+is+fear+itself&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=the+only+thing+we+have+to+fear+is+fear+itself&btnG=Search&meta=)

---

### Post by gazzadtfan on 2007-11-16
Hi

what I'm trying to get at is this. I want a clean install on a second hard drive which has 3 partitions. System, /home and swap. The last time I tried the clean install it caused all sorts of problems but I wasn't sure if it was the way I did it or did I miss something out. 

What I did was to format the System partition, during the install and put the new version of Ubuntu on that partition with no changes to size or anything. I did that and I had problems getting the internet and resolution etc. so I did the same install back to 7.04 using the 7.04 disc.

After that I couldn't load XP because of the mbr problems. Basically I want to clean install 7.10 and hopefully have no problems with the mbr but wanted to know what the best way to do that is.

Cheers

gazzadtfan

---

