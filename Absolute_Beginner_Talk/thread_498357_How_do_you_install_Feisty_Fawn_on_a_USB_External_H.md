---
title: "How do you install Feisty Fawn on a USB External Hard Drive?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by APer3Caper on 2007-07-11
Hello everyone. I'm a new Ubuntu user. Well not that new but I've never been sucessful in installing Ubuntu. I've been trying to install Ubuntu on an external USB hard drive. My main hard drive doesn't have much space on it since Windows takes up most of the space and I'd like to leave Windows alone. I purchased a 100 GB Seagate external USB hard drive and tried multiple times to install Ubuntu on it. Each time something went wrong. One time I completley destroyed my MBR and was luckily able to restore it. I've followed these [instructions]("http://ubuntuforums.org/showthread.php?t=495145") to install Ubuntu on an external hard drive from Megaqwerty but got hung up on step 4 and the intructions were for Dapper Drake. I was wondering if anyone knew how to install Feisty Fawn on an external hard drive. I have an IBM Thinkpad R40 with 768MB RAM. Any help would be greatly appreciated. Thank you!

---

### Post by confused57 on 2007-07-11
> **APer3Caper said:**
> Hello everyone. I'm a new Ubuntu user. Well not that new but I've never been sucessful in installing Ubuntu. I've been trying to install Ubuntu on an external USB hard drive. My main hard drive doesn't have much space on it since Windows takes up most of the space and I'd like to leave Windows alone. I purchased a 100 GB Seagate external USB hard drive and tried multiple times to install Ubuntu on it. Each time something went wrong. One time I completley destroyed my MBR and was luckily able to restore it. I've followed these [instructions]("http://ubuntuforums.org/showthread.php?t=495145") to install Ubuntu on an external hard drive from Megaqwerty but got hung up on step 4 and the intructions were for Dapper Drake. I was wondering if anyone knew how to install Feisty Fawn on an external hard drive. I have an IBM Thinkpad R40 with 768MB RAM. Any help would be greatly appreciated. Thank you!

If your bios is capable of booting first to your external drive, set it to boot your USB drive before your internal hard drive...before you boot the live cd to install Ubuntu.  You should be able to do a normal install this way...when you reach the screen to install grub, click the "Advanced" button, then type in:
```
/dev/sdb
```
or however the partitioner recognizes your external hard drive...Megaqwerty's instructions are excellent and would probably be needed for someone with a USB powered external drive...if your drive has an external power source(plugs in to an outlet), then you should be able to do a normal install.

---

### Post by yanqui on 2007-07-18
A normal install didn't work for me when I was putting Dapper on a USB hdd, the reason is that the usb modules need to load in a certain way, that's the reason for step 5.

---

