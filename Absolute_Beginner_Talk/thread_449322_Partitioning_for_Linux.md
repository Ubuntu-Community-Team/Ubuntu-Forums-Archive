---
title: "Partitioning for Linux"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-05-20
Well, here goes. I've read some of the FAQs, and also Herman's pages, and I get the general drift of how to go about doing a dual-boot XP Pro - Linux setup. But there's a part of the process that I'm wary of, and I'd appreciate any comments/help from the experts here.

I have an 80Gb main drive, which is partitioned nearly 50/50. The primary patition is FAT32, and has Win XP Pro installed. The other is formatted NTFS, and has only data, which I can move to another drive with no problem.

Question - do I use Ubuntu's partitioning program to make the 2nd partition free space, and install Ubuntu there, with the Windows sharing partition and Swap partition as well as the / partition? I understand  the space required for each of the partitions, which in my case will be rough;y 38Gb for /, 10Gb fpr Sharing FAT32,  and 2Gb for Swap - based on 2x RAM.

Now, I also have a USB external 80Gb drive, formatted NTFS, but with no data, so I could use it entirely for Ubuntu. Is it straight forward to make this into free space and do the partitioning with Ubuntu's  manager? The drive is always attached and switched on. Would Grub configure the dual boot OK in this instance?

My hesitation in all this is living in a very small town, no Linux information available that I know of, and quite a distance to a bigger town, where there probably isn't any better prospects for support. So it will be cold turkey for me, and it coud turn out bad if I'm not careful.

I have an Apple as well as my PC, so I could use the 'Net for reference when I do the install. That might prove to be a real help, but if I can at least make an informed start I'm less likely to make a giant hash of things.

From what I see of these forums, newbie help is generally forthcoming and kind. I hope someone can respond to my questions, and I can join the Ubuntu community. Awaiting anyone's suggestions with interest.

---

### Post by overdrank on 2007-05-20
Question - do I use Ubuntu's partitioning program to make the 2nd partition free space, and install Ubuntu there, with the Windows sharing partition and Swap partition as well as the / partition? I understand  the space required for each of the partitions, which in my case will be rough;y 38Gb for /, 10Gb fpr Sharing FAT32,  and 2Gb for Swap - based on 2x RAM.

Now, I also have a USB external 80Gb drive, formatted NTFS, but with no data, so I could use it entirely for Ubuntu. Is it straight forward to make this into free space and do the partitioning with Ubuntu's  manager? The drive is always attached and switched on. Would Grub configure the dual boot OK in this instance?

Hi and welcome, partitioning a drive is up to you but what you have purposed sounds good.
This link may help also
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
I personally would use the partition you described and keep the external drive for backup and storage. Hope this helps and good luck!

---

### Post by Kobalt on 2007-05-20
Hello,

The easier solution for you, in my opinion, would be to leave windows in its half of the HD (the internal 80G one) and set the Ubuntu installer to use the other half (it will partition it, with swap etc., just fine and all by himself). And I would use the external HD as a sharing drive for data between Ubuntu and windows. 
The is really the simplest solution, since you don't know much (yet!) about Linux/Ubuntu.

If you need some additional help/info, check [this]("http://psychocats.net/ubuntu/partitioning") out.

---

### Post by mikewhatever on 2007-05-20
> Question - do I use Ubuntu's partitioning program to make the 2nd partition free space, and install Ubuntu there, with the Windows sharing partition and Swap partition as well as the / partition? I understand the space required for each of the partitions, which in my case will be rough;y 38Gb for /, 10Gb fpr Sharing FAT32, and 2Gb for Swap - based on 2x RAM.

You've got it all figured out. :)
If you go for the external drive, either resize or erase the partition there and make the ones you've planned above. The only tricky thing with it is GRUB. It should be installed to the MBR of the external HDD and the boot sequence set so that the PC tries to boot from the external and then from the internal HDD. If GRUB is installed to the MBR of the internal HDD, the system should still work as long as the external one is connected. When it is disconnected, you'd get error 21, because GRUB will be looking for its part in /boot/grub on the root partition which is currently not present.

---

### Post by drowner on 2007-05-20
I agree, whole heartedly, that the simplest thing to do would be to install ubuntu to the internal hard drive, and use the external one for the shared space and back up. THis makes much more sense.

---

### Post by corowakid on 2007-05-20
Well, true to Ubuntu's reputation, prompt responses that I can understand, making me a *lot* more confident with getting under way.

My thanks to all who replied - hopefully with time I'll develop some knowledge that I can share with others.

But, tomorrow (me being a retiree), with a forecast of rain, so confined indoors, its "Ubuntu, here I come"!

---

### Post by Kobalt on 2007-05-20
Welcome to Ubuntu :)

---

### Post by overdrank on 2007-05-20
> **corowakid said:**
> Well, true to Ubuntu's reputation, prompt responses that I can understand, making me a *lot* more confident with getting under way.

My thanks to all who replied - hopefully with time I'll develop some knowledge that I can share with others.

But, tomorrow (me being a retiree), with a forecast of rain, so confined indoors, its "Ubuntu, here I come"!

Welcome and good luck!:popcorn:

---

