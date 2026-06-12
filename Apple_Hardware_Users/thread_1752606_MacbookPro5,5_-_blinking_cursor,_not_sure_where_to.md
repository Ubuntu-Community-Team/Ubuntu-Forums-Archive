---
title: "MacbookPro5,5 - blinking cursor, not sure where to go"
date: 2011-05-08
forum: Apple Hardware Users
---

### Post by isucompositeur on 2011-05-08
Hi folks,

I'm trying to get Natty running on my MacbookPro5,5. I originally installed the 32-bit version, which came off without a hitch. I hadn't intended to do this and wasn't paying attention--didn't realize it until I was setting up a VM in VirtualBox and it only showed 3GB of memory available.

So I downloaded and installed the AMD64 disc instead. After this install, I noticed that there were now two Linux selections in the rEFIt menu, and any time I try to boot one, all I get is a blinking cursor in the upper-left corner.

I've tried following the instructions in the FAQ that seem to pertain to this issue. When I run the Partition Tool in rEFIt, it tells me the partitions are synced. I also tried reinstalling grub, but grub refuses to reinstall when I attempt to do so from the LiveCD; I don't remember the exact error.

I'm just wondering what happened between the 32-bit and 64-bit versions? The only thing I can think of is that I wasn't paying attention with the 32-bit install and installed grub to the MBR instead of the Ubuntu partition (which I'm sure I did in the 64-bit install), but I'm afraid to test that theory out because I'm not really in the mood to nuke my OS X install and have to restore backups.

Has anybody run into this issue with Natty, or is there any insight? Is it safe to install the bootloader to /dev/sda instead of choosing the Ubuntu partition explicitly?

Thanks!

---

### Post by Silmathoron on 2011-05-08
I don't really understand what went wrong, however, I installed grub on /dev/sda and I don't have any issues with that...
Try to search in older threads, I think I saw some questions that look like yours, maybe somebody already answered

---

