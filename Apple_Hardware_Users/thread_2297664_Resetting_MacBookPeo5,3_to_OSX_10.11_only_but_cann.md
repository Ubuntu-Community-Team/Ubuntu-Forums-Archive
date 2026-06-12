---
title: "Resetting MacBookPeo5,3 to OSX 10.11 only but cannot remove GRUB2"
date: 2015-10-05
forum: Apple Hardware Users
---

### Post by Carty_Ellis on 2015-10-05
Now that I have Ubuntu 14.04.3 running with rEFInd, I want to go back to just OSX 10.11.  

I have removed the Linux and Linux Swap partitions from the HD with Live_Gparted.  

I have successfully removed rEFInd by removing the ./EFI/refind directory.

Straight booting on power up invokes GRUB2.  EXIT gets me past it and OX boots fine.

Option key on power up will bypass GRUB2.

I cannot do recovery options, because of the GRUB2 interference.

( MacBookPro5,3 )

Looking over all the posts in this forum, no one seems to have successfully removed GRUB2.

Any other choices besides wiping my HD and doing a Time Machine recovery?

---

### Post by Carty_Ellis on 2015-10-07
Resolved by erasing the hard drive and reinstalling OS X 10.11

---

