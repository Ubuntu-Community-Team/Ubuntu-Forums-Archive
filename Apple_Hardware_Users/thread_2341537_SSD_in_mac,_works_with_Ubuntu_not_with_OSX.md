---
title: "SSD in mac, works with Ubuntu not with OSX"
date: 2016-10-29
forum: Apple Hardware Users
---

### Post by stu.edwards on 2016-10-29
Hi All,

I have a 512 Vector OCZ SSD, it had Ubuntu and El-Capitane installed side by side. I suspected it became corrupted as my mac crashed and I then got the crossed out circle when trying to load OSX.

The ubuntu partition still works fine and the drive is detected fine. I wiped the drive and installed a fresh copy of Ubuntu, then shrunk the partition and made an hfs+ partition in gparted ready for a clean install of OSX. Now whenever I load the OSX disk utility from a bootable USB, the drive is not detected by OSX.

Any ideas why this drive seems to function fine under Ubuntu but cannot be detected in OSX. If the drive was faulty/failing I would have thought I wouldn't be able to see it in Ubuntu either.

Thanks,

Stuart

---

### Post by daftykins on 2016-10-30
Hi

Were it me, I would most likely wipe the drive entirely and see if Disk Utility changes its' mind. I would also add a PRAM zap to be a little more sure.

Failing those, I would double check which drive firmware version you are running and see if anything newer is available from OCZ.

Good luck!

---

### Post by coffeecat on 2016-10-30
> **stu.edwards said:**
> I wiped the drive and installed a fresh copy of Ubuntu, then shrunk the partition and made an hfs+ partition in gparted ready for a clean install of OSX.

When you wiped and installed Ubuntu, is it possible you replaced the partition table? If the partition table is now ms-dos, it's likely that MacOS El-Capitan would refuse to recognise an HFS+ partition there. An HFS+ partition in a disk with a ms-dos partition table is the ultimate red-headed stepchild, and my guess is that MacOS is simply confused by the combination.

You need a GUID partition table (GPT) for booting MacOS. Furthermore, I would not choose to create a HFS+ partition using Gparted for MacOS to boot from. Far better to use the MacOS Disk Utility.

Bear in mind that I haven't touched an Apple machine for some years, but my approach would be to wipe the drive and partition it in MacOS Disk Utility first, creating sufficient partitions for your Ubuntu installation as well. MacOS' Disk Utility won't be able to create Linux filesystems, of course, but you could create spare partitions with whatever filesystem is to hand in Disk Utility. When you come to install Ubuntu, you simply reformat those partitions you need as ext4, swap, or whatever you need.  

When you partition the drive in MacOS Disk Utility, make sure you choose "GUID Partition Map" (it'll probably default to that), and make sure that it creates an EFI partition (I'd be surprised if it doesn't, but it'll probably be hidden) so that you can install Ubuntu in EFI mode. Whether you should install MacOS or Ubuntu first, I don't know. As I said - it's been quite a few years.

By the way, what type of Mac are you using, and are you using the 512 Vector OCZ SSD as the internal HD on the Mac?

---

