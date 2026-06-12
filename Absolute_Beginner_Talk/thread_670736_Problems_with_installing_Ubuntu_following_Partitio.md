---
title: "Problems with installing Ubuntu following Partition Magic"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Paul Cooper on 2008-01-17
Hi. 

I'm new to all this. I need XP for work, but would really rather not have it as my main OS. So I used Partition Magic to set up partitions for XP, a fat partition for Boot Magic, and the primary partition for Ubuntu plus the share partition etc, as the software recommended. 

Trouble was, when I tried to boot Ubuntu from the live CD, it seemed to want to install into the small partition that I had set up for XP, and when I selected "manual" for choosing the partition for the installation it told me no root drive had been allocated. I was then a little out of my depth, but then things got worse when "ubiquity" crashed (this happened every time I got to this part). 

I don't suppose anyone with any experience on this could guide me through this section of the install: it would be much appreciated. I really don't want to be consigned to Windows hell all the time.

---

### Post by p_quarles on 2008-01-17
The bootloader used by Ubuntu is fully capable of multi-booting, and will even detect and boot your Windows partition for you. :)

The easy way to do this is like so:
1) Format the drive so it's clean (assuming there's no data on it)
2) Install Windows. Don't worry about pre-partitioning, as the Ubuntu installer can resize any existing partitions.
3) Install Ubuntu, and when you get to the partitioning options, select "resize existing partition and use freed space." 

If everything goes right (usually does, but YMMV), you'll have a dual-boot system ready to go.

Finally, if you do continue to encounter errors with the Live CD, I would recommend using the alternate CD. For certain hardware, it makes things much easier.

---

