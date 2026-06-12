---
title: "Help with external booting"
date: 2010-02-09
forum: Apple Hardware Users
---

### Post by shiink on 2010-02-09
I have been working on getting an external install to boot on my macbook 4,1. I have followed the tutorial shown [[COLOR="Navy"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1376277").

So far i have been able to successfully install ubuntu to a partition on this harddrive and what appears to be a proper configuration of grub to boot this partition. The problem occurs after I execute the menu entry in grub and it proceeds with the boot process. After a screen of text scrolls down, the process then hangs and I get a couple errors. 

Sometimes I get an error referring to checking the battery status. However, the last time I attempted to boot I received errors similar to this:

usb_id [831]: unable to access '/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input6/event6'

and

[216.049852: I/O error, dev sdb, sector 1569427
...buffer I/O error on device sdb4, logical block 174089
"echo 0> /proc/sys/kernel/hung_task_timeout-secs" disables this message.

These errors display with some slight variation, but this is essentially this is what I'm dealing with. I am not sure where to start with this problem since I am relatively new at this and do not completely understand what could be causing this.

---

### Post by linuxopjemac on 2010-02-10
the only thing that I can say is that not all Macs can boot from USB as they don't have the firmware to do so. I am not sure about the macbook 4,1. You have to find out by googling or so.

---

