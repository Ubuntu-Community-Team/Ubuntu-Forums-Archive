---
title: "No option to install the boot loader (grub) to /dev/sda3"
date: 2010-11-28
forum: Apple Hardware Users
---

### Post by pu-erh on 2010-11-28
Dual-Boot: Mac OSX and Ubuntu

Want to dual boot 10.04LTS and OS X 10.6.5
But there is no option to install the boot loader (grub) to /dev/sda3 as per the following
using Bootcamp 

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by sikander3786 on 2010-11-28
It shoud be last step just before it start the installation process.

Do you see the Advanced button? What does it list there?

---

### Post by beefinit on 2010-12-03
Hi,
I have, what sounds to be, the exact same problem. 

I am installing Ubuntu 10.04 dual boot with Mac Os X 10.6.5.

I am setting up my partitions manually.

1st partition dev/sda1 is EFI/GPT partition (I'm using rEFIt) (~200mb)
2nd partition dev/sda2 is hfs+ (mac 0X x partition) (~270 GB)
3rd partition dev/sda3 is ext4 (main ubuntu 10.04 installation) (~29 GB)
the last partition is the swap area (~4.2 GB)

So ubuntu is installed on the /dev/sda3 partition. However, when you go to the advanced tab during installation to specify where to install the bootloader, the default is /dev/sda. I can scroll down and select /dev/sda3 BUT then the OK button is grayed out, not allowing me to make this selection. So instead, I unchecked the "install bootloader" box and continued. Now I have linux installed with no bootloader and hence no way to launch. I think the only solution is to install grub2 manually in /dev/sda3 using the ubuntu live CD. Is this correct?

Why doesn't ubuntu let me install the bootloader where I want to?

note:
I also tried installing the bootloader in /dev/sda1, but this did not work, so I purged grub from that partition and then used the mac osx start up disc to repair the HD.

---

### Post by linuxopjemac on 2010-12-04
just put it on /dev/sda
it worked for me..

I also recommend to downgrade Grub 2 to Grub legacy, Grub 2 gave me constant headaches.

---

