---
title: "Ubuntu 13.04 doesn't boot on Macbook Pro 17&quot; after installing"
date: 2013-09-29
forum: Apple Hardware Users
---

### Post by IvanPsy on 2013-09-29
I just installed Ubuntu 13.04 on my Macbook Pro 17" (a Mac 5,2) but it freezes at the beginning: when the dual boot appeared (OSX and Ubuntu) I selected Ubuntu, then a blank screen with a penguin picture appeared, then it stopped with this screen.

I had to turn off the Mac by long pressing the button.

I tried again, and when I selected the Ubuntu OS a message appeared:
"Missing operating system".

I tried a third time: again it freezed with the blank screen and the penguin.

No problems with the OSX partition. 

What's happening?

I follow this guide:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

BTW: I had some trouble about the location of the bootloader during the installation: I had been able to choose between 2 partitions: the Ubuntu position and am EFI partition.
Both led to the same results.

---

### Post by petersphilo on 2013-10-04
the bootloader should be installed at:
/
on your Ubuntu partition.
Make sure you also elect to format the Ubuntu partition (ext4 is best)
also install refit (or refind)

---

### Post by IvanPsy on 2013-10-04
> **petersphilo said:**
> the bootloader should be installed at:
/
on your Ubuntu partition.
Make sure you also elect to format the Ubuntu partition (ext4 is best)
also install refit (or refind)

Thank you!

I solved by letting Ubuntu automatically partitioning and filling the HD empty space.

I had to install from boot, not from LiveCD.

All worked well... :-)

---

### Post by asifnaz on 2013-10-05
You should have used it in the first place

---

