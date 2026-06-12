---
title: "Dual Boot &amp; Switch"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2007-01-27
I currently have XP on a IBM z50m andwould like to add Ubuntu on a second partition.  I have Ubuntu on a second computer and I like it very much and would really enjoy be able to have it on my laptop with XP.
 1.  Can you install Ubuntu 6.10 so that it will partition the drive and not change anything about the exsisting XP and will let XP be the "Default" boot configuration.
 2.  Has anyone installed Ubuntu on this laptop before?

Really appreciate any assistance.

John:D

---

### Post by ENN0 on 2007-01-27
Ubuntu comes with a partition programe so when you install it it automaticly partitions the drive!

---

### Post by xpod on 2007-01-27
You can chose the "resize current partition" at the partitioning stage and it will resize your existing Windows install whilst automatically setting up your dualboot for you.

It`s best to defrag Windows a couple of times first just to be sure you`ve no data getting lost at the end of the drive.
Never actually had to do it that way so i might be a bit off but it`s something like that:D

---

### Post by Tomosaur on 2007-01-27
Yes, defrag your Windows stuff and back up anything important. It would also be wise to make sure you have some method of recovering XP if anything goes wrong. It's not likely to, but better to be safe than sorry.

After you've defragged and backed up, boot from the LiveCD and start the installer. It'll eventually ask you about partitioning. You can choose the resize option, or to manually edit the partition tables. I prefer the manual method. You need to shrink your NTFS partition, make at least one partition for Linux (I reccommend formatting this partition as ext3), and another partition, which should be around twice the size of your RAM, and format this as swap. Apply the changes, and then set root, signified by a forward slash, to the ext3 partition, and swap as the swap partition. It will probably automatically select those settings for you, but that's what you should do in case it doesn't. Finish your installation, and reboot. It will automatically try to boot Ubuntu - let it. Once it's done, you can open /boot/grub/menu.lst and edit the 'default' line to make Grub boot Windows by default. Grub counts from zero, so first item in the grub menu is 0, second is 1, third is 2, etc etc etc. Remember that the 'Other Operating Systems' line is included in the count.

Alternatively, download and install the program in the link in my sig :)

---

### Post by johnfarrow on 2007-01-27
Thanks for your help.  Anyone on Item #2 in original post?

---

### Post by johnfarrow on 2007-02-16
tried to set XP as default boot but it said  no program was avail to open  /boot/grub/menu.lst and edit the 'default'.  What program do  use to "open with"?

---

### Post by tbasherizer on 2007-02-16
Use gedit or Kate to edit the file. I don't know what to enter to change the default, because the last time I did that was ten months ago.

---

