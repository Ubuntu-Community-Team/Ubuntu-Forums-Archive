---
title: "Setting up a Desktop 14.04 on an unresponsive ubuntu 12.10 partitioned in MacbookPro"
date: 2014-04-27
forum: Apple Hardware Users
---

### Post by ege2 on 2014-04-27
Since I couldn't resolve my unresponsive(blank screen) boot up problem of the unsupported 12.10 in my 40 gb partition within MacbookPro 8,2.

I've decided to download 14.04 and will try to set up on the 40 gb partition of my harddrive.

How could I set up the new 14.04 without using the unresponsive 12.10 interface?

---

### Post by jamesisin on 2014-04-29
Do you have enough space to create an additional reasonably sized partition for 14.04 to live?

---

### Post by Vinodh Moodley on 2014-04-29
Use UnetBootin to create a bootable USB installer. Just format a USB flash drive to FAT32, open UnetBootin and select the Ubuntu ISO and select the USB drive. Once the installer is done, reboot and hold down the Option (alt) key. Select EFI boot and install. Choose the "something else" option for partitioning and make sure Ubuntu is installed to the correct partition. Create a SWAP partition as needed. Once Ubuntu is installed, restart to your new Ubuntu desktop or hold down the Option key to get back to OSX.

NOTE: Use the normal 64bit Ubuntu ISO, not the "Mac" ISO. The Mac ISO does not support EFI and uses BIOS emulation.

---

