---
title: "Duplicate Linux icons in rEFIt..."
date: 2006-08-06
forum: Apple PPC Users
---

### Post by hajk on 2006-08-06
I'm running Ubuntu Dapper on a MacBook, using the rEFIt boot manager with a dual boot setup. Dapper is installed on an HD partition made first with Boot Camp, then converted to Linux ext3 during the Dapper install. This partition shows up as /dev/sda3; the other partitions are for OS X (/dev/sda2) and the rEFIt boot manager itself (/dev/sda1). These three partitions use the entire HD, there is no unallocated space left (I'm using a swap file on the Linux partition, not a separate swap partition). I use LILO to boot Dapper, which I installed to the MBR of /dev/sda with "lilo -b /dev/sda".

Now, whenever I boot, the rEFIt menu shows three icons (boot options):
(1) OS X from HD; (2) Linux from HD; and (3) Linux from partition #3.
I can start Dapper from either of the duplicate Linux icons. 

Yet, it bugs me to no end that there are these two, near identical, Linux boot options, that nonetheless refer to the same OS. Does anybody know how to remove one of them?

---

### Post by sglynnsp on 2006-08-07
hajk. I have a similar issue, and although I can't offer a solution to it, I can maybe provide a hint as to why it happened. In my case, I typed in the wrong lilo command, and it seemed to write boot information in a different location to when I then typed the correct lilo command. Then on reboot, rEFIt picked up both and showed the two icons. I can't figure out how to delete the duplicate boot info though. Hopefully someone can offer a suggestion.

Regards
Simon

---

### Post by hajk on 2006-08-08
Well, I reinstalled Ubuntu and now did a few things differently: (1) installed LILO with "lilo -b /dev/sda3 -P ignore", and (2) installed rEFIt at the very end, after Ubuntu completely installed. And YES, there is now only a single Penguin icon with "Linux from partition #3" moniker.
My complete installation report is at [http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk"). I now have only one worry left: the MacBook is running very hot after a few hours, much more so then under OS X.

---

### Post by chasisaac on 2006-08-08
> **hajk said:**
> I
Now, whenever I boot, the rEFIt menu shows three icons (boot options):
(1) OS X from HD; (2) Linux from HD; and (3) Linux from partition #3.
I can start Dapper from either of the duplicate Linux icons. 



Reinstall from scratch. Pain the %#(%$*@.

---

### Post by hajk on 2006-08-09
Yes, I did. Installed LILO with "sudo lilo -b /dev/sda3 -P ignore", and now just a single Penguin icon shows up in rEFIt.

---

