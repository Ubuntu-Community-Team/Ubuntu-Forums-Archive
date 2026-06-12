---
title: "MacBook Pro 4,1 booting from USB HDD"
date: 2009-05-04
forum: Apple Hardware Users
---

### Post by paulcartman on 2009-05-04
Hi guys.
I've got a MacBook Pro 4,1 (Intel based) and external USB HDD (WD). But I've also got a simple PC and I want use Ubuntu Linux 9.04 on both systems.

I've try to create several partitions on external HDD (1st - rEFIt, 2nd - Linux **/** mount point, 3rd - user space partition with HFS+ file system). Then I've install rEFIt (HFS+ file system, install from Mac OS X) to 1st partition and install  Ubuntu 9.04 (boot from CD) to 2nd partition on external HDD. Also I install boot loader to /dev/sdb (this is same disk, that has rEFIt and Ubuntu).

After turning on my Mac, I hit option key and see boot menu with Mac OS X and rEFIt boot logo. Then I choose rEFIt item and see second boot menu when I see standard rEFIt loader. I choose Partition Tool to update partition scheme and after that I choose Linux system to load. And after that.... nothing! "Operation system not found"...

What I'm doing wrong? How can I boot linux from external USB HDD on my mac and how I must setup boot loader to use this system on mac and PC systems?

Thank you and sorry for my english))

---

### Post by cyberdork33 on 2009-05-04
it will not be easy to do what you are asking... In fact, I don't think we are there yet as far as making a system that you can just take back and forth between two machines (one being a mac) and have everything work properly.

If you want to boot Ubuntu form an external drive, the best way is to boot via EFI, and this is not possible with other PCs. See the FAQ for Intel Macs in this forum for information on booting via EFI.

---

### Post by 3dgimp on 2009-12-01
My friends macbook has died on him, and wont let him login. I've copied the 9.04 iso contents to the usb and run the makeboot.bat to make the drive bootable but the mac doesnt seem to pick it up. 

What am I doing wrong? Is this even possible?

---

### Post by linds2009 on 2009-12-02
I'll give those a try!
Thank for sharing\

---

