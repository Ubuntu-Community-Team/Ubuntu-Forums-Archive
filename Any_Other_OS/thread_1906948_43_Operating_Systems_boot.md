---
title: "4/3 Operating Systems boot"
date: 2012-01-10
forum: Any Other OS
---

### Post by arjunrj405 on 2012-01-10
Hie every body first of all...
1) I dont know if I am posting on right forum (if not please suggest):popcorn:
2) I explain my problem in following processes.
[CENTER]a)MY PC:
Intel Pentium(R) Dual-Core CPU E5500 @ 2.80ghz
2038MB RAM
no graphics card
(can give you more information)

b)I installed Microsoft Windows XP Professional on 30 Dec 2011.

c)Then, I installed Microsoft Windows 7 Ultimate **on another drive** on 7 Jan 2012

d)On 10 Jan 2012, I installed Ubuntu 11.10 on Windows 7 as an application.

e)Tomorrow i.e on 11 Jan 2012 i wish to install Windows Vista on Another Drive as i like it and i dont have much data to keep in hard drive(You can call me mad if you like). Will I be able to do it...

f)Problems that i think i may face:
=>Windows 7 came after Vista so maybe I must have installed it before
=>4 OS on a PC!(Am I mad or what!... lol)
=>Please suggest dear firs/madadams...........:D
[/CENTER]

---

### Post by CharlesA on 2012-01-10
Good luck. You shouldn't run into any problems, but I don't see why you'd need both 7 and Vista when both of them are very similar.

---

### Post by Basher101 on 2012-01-10
you will need to restore grub as it will get overwritten on your vista install. Here is the easiest method to do so: [http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html](http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html)


regards

---

### Post by arjunrj405 on 2012-01-10
> **CharlesA said:**
> Good luck. You shouldn't run into any problems, but I don't see why you'd need both 7 and Vista when both of them are very similar.
I love Vista's graphics my friend.
Windows 7 and XP i keep for they are fast in different situations.
Thankyou for guidance:P

---

### Post by arjunrj405 on 2012-01-10
> **Basher101 said:**
> you will need to restore grub as it will get overwritten on your vista install. Here is the easiest method to do so: [http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html](http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html)


regards
Friend;
Will it happen even if i have installed ubuntu as an application on windows?8)

---

### Post by Basher101 on 2012-01-10
> **arjunrj405 said:**
> Friend;
Will it happen even if i have installed ubuntu as an application on windows?8)

*facepalm* sigh...i gotta read the posts more carefully :D

+1 for cloning the drive, if you get a worst-case-scenario where everything does not work (not even backups) you still got something you can roll back to.

---

### Post by oldfred on 2012-01-10
You need to understand how Windows multi-boots. It uses just the one active partition (boot flag in Ubuntu). With multiple drives I am not sure if it will still only boot from one or one per drive.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I have used a Windows 7 repairUSB to run chkdsk on my XP, so you really need a repairCD or USB.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Food for thought:

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

