---
title: "desperate alterations to my external HDD"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by micfreedom on 2007-04-29
:(   Dear ubuntu friends, 
My system AMD Duron 1.19 GHz, RAM 256 Mb, O/S Windows XP Home SP pack 2.

I have an external drive WD My book 500 GB. 
I used GParted where it asked me whether i wanted to create a device from which to boot. I putyes.

Next, I tried to partition with GParted 's own types of partitions. it seemed to take ages without nothing happening.#
I stopped the process after an hour. I tried to start the ubuntu CD klive and install from there. When I reched the partition bit, i chose the the partitioning of the External Hard drive with ubuntu specifications of partions to be made.
There too, it satred but after an hour, the indicator still read 5%. 
So I thought I would try to use Windows again and repartition with GParted in windows. But I cannot boot windows, even when I alter the BIOS to boot from EIDE 0. I tried the Linux rescue disk, the Windows rescue disk and finally , in desperation, the original Windows XP disk, physically taking the USB plug off and taking the WD My Book plug off to islolate it so it would not influence the booting.
I cannot get into Windows anymore. I am writing this from my wife's computer which is healthy!!!
What will I have to do to go back to the "normal" installation process.
(I'd like very muc to install Ubuntu Feisty Fawn!)

---

### Post by NeoTaoistTechnoPagan on 2007-05-01
Is your external HDD plugged into a USB2-capable port? I made the same error with my USB HD install when I first started. If you can boot from the CD, then plug in your USB drive, GPartEd should let you partition it and it shouldn't take anywhere near that long.

If it's USB the drive will most likely be seen as /dev/sda - I'm not sure about Firewire since I don't have any of those here.

---

