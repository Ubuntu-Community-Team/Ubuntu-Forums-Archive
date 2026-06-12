---
title: "Uninstalling GRUB on a partition? EFI gone?"
date: 2009-06-24
forum: Apple Hardware Users
---

### Post by el.otro on 2009-06-24
I recently reinstalled Ubuntu 9.04 on a Mac Pro, but feeling so confident I didn't pay attention to the last option to install the boot loader on sda3, and it started booting directly to GRUB instead of giving me the option on the mac EFI.

I think the firmware itself is not corrupted on any way, because it does work for me when I press the option key: then it says Machintosh HD and "Windows", and lets me boot any of the two OSs.  I also went and made sure I had GRUB installed on ubuntu's partition, and to make things esier I installed rEFIt and syncked the partitions, and its all working OK.  

BUT....the computer is shared and I would like to remove the "anoyance" of using the third-party rEFIt if I could use the actual mac EFI...AND uninstall GRUB from hd0.

I found somewhere to uninstall GRUB with the following command:

```
dd if=/dev/null of=/dev/sdX bs=446  count=1
```but I am not confident, since I have never used the dd command and it has a different syntax.  What I understand is that it's sending a copy of the "null" device to sd(x) (a1? in my case),* bs* is the blocksize (?) I don't understand the 446 there; and then *count* is the number of blocks.   I can see its function, but doesn't that remove the partition itself? could that corrupt the disk? is GRUB installed on the same partition than EFI? Is grub somehow a group of files that I can browse to and delete myself?  There is a FAT partition with a name "EFI", is that where grub was installed?

I feel like it is very simple, but I don't think that command could do it.  I haven't found enough about "blessing", and I have a feeling it is important. 

Thanks beforehand for any help

---

### Post by Richardcavell on 2009-06-24
Hi.  I'm not sure what it is that you want.  Could you clarify what you want the final arrangement of your computer to be?

As I understand it, what you want is for your computer to automatically boot into OS X, but you want to have the option of holding down option in order to boot Linux.  Here's how you do it:

Simple way is to go into OS X, and then go to System Preferences, Startup Disk and select your OS X partition as the place to boot from.  Then click 'Restart'.  Now your computer will boot straight to OS X without giving you the Linux option explicitly.  You'll have to hold down option at boot time to make your Linux partition appear. 

You need GRUB on the Linux partition.  Not the MBR; the Linux partition.

Richard

---

### Post by el.otro on 2009-06-24
I had figured it out, and THEN read your response.  You're right: that's all I needed to do.  I changed the boot disk and deleted rEFIt.   GRUB was on the linux partition and it booted OSX by default...

I have a tendency to make things more complicated (but it was a matter of my ignorence, after I read a little about grub and checked my config, I realized what it was), next time I'll read more before posting!

Thank you very much

---

