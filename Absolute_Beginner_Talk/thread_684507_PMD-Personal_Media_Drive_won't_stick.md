---
title: "PMD-Personal Media Drive won't stick"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by jloveless on 2008-02-01
I have a dual boot HP 7760 with a Personal Media Drive slot. (it is actually a USB slot and the drive that goes in there can also be used as a standard external USB drive on any computer.)

My problem is this. I couldn't mount the drive at first without going into Windows and "Removing Safely" - a practice I hadn't always done. I did so and then I removed the drive and rebooted into Linux (Ubuntu 7.10). I inserted the PMD and it was recognized, mounted, and I can use it like any other drive. It is great for storing data and such. I also want to use it for backups. When I start Linux now, however, the drive isn't recognised automatically but I need to remove and reinsert it for mounting to be done. Most of the time it is recognised then, but not always. My objective is to leave the drive in the slot most of he time and be able to use it with Vista and with Linux. The PMD for use with Linux is 300GB and I also have a 750GB PMD that I use for Vista and work backup. I have to use Vista to connect to my work environemnt but I try to use Ubuntu for everything else.

Any ideas on how I can get it to stick so that I don't have to remove/reinsert each time?

Thanks.

---

### Post by dcstar on 2008-02-02
> **jloveless said:**
> I have a dual boot HP 7760 with a Personal Media Drive slot. (it is actually a USB slot and the drive that goes in there can also be used as a standard external USB drive on any computer.)

My problem is this. I couldn't mount the drive at first without going into Windows and "Removing Safely" - a practice I hadn't always done. I did so and then I removed the drive and rebooted into Linux (Ubuntu 7.10). I inserted the PMD and it was recognized, mounted, and I can use it like any other drive. It is great for storing data and such. I also want to use it for backups. When I start Linux now, however, the drive isn't recognised automatically but I need to remove and reinsert it for mounting to be done. Most of the time it is recognised then, but not always. My objective is to leave the drive in the slot most of he time and be able to use it with Vista and with Linux. The PMD for use with Linux is 300GB and I also have a 750GB PMD that I use for Vista and work backup. I have to use Vista to connect to my work environemnt but I try to use Ubuntu for everything else.

Any ideas on how I can get it to stick so that I don't have to remove/reinsert each time?


Possibly not if the kernel isn't recognising it reliably with your hardware - the next Ubuntu version (8.04) due to be released in April may be better as it will have a later kernel.

As an option, you may want to consider installing VMWare server in Windows and run Ubuntu as a VM, then you can access the USB device via the Windows hardware (as you simultaneously run Ubuntu).

---

