---
title: "My system hangs after..."
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Drewstain on 2006-04-13
Pardon me. I just wanted to revive my old system, but it appears that I migh just have to take it back to its dark corner as it hangs when I tried Ubuntu.

The system is an old Dell
Processor 550
96M SDRAM
10.2 GB HD
CD rom
64M TNT video card

I found Ubuntu 4.1 and it appeared to have install great, then it asked if I wanted to download all the packages via internet to which I said yes. After all the downloading it re-started, but the monitor is just black/blank so I do not know what to do. I have done this procedure three times so now.

As I decided to pay more attention when the system starts, I found the following:

GRUB loading stage 2

Starting hotplug subsystem
Modprobe: Fatal: Error inserting pciehp (/lib/module/s.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permited

Modprobe: Fatal: Error inserting shpchp (/lib/module/s.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permited

So it looks like this module is not being loaded for whatever reason

At the very bottom I can barely see something like #something login: but then the monitor goes blank.

I have no clue what this means as this is my first try at something other than Windows.


Does any one have any sugestions? I really do not want to spend over $100 just to upgrade the memory but if that is the issue, then I guess that is the end for that system.

When I tired to install Kubuntu I did not even make it to install stage 1 so I went for Ubuntu 4.1 instead.

Respectfully,
Drew

---

### Post by Qrk on 2006-04-13
Ubuntu 4.10 is over a year old... right now the stable version is 5.10. If you can, I suggest you get that version, named breezy. You can order a CD through shipit if you cannot download it yourself, otherwise you can download it at [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Now on to your problems. I do not believe those errors are the cause of your problem. Ubuntu Warty, which you have, uses a different xserver than Breezy. 

Once your screen goes blank, try pressing <Ctrl><alt><F1> If the problem truely is with the xserver, you should get to a text based login prompt. Enter you username and password, then issue this command:

```
sudo dpkg-reconfigure xserver-xfree86
```

Take note of what driver is selected. You should probably select vesa... as that driver has the best support for older hardware as it doesn't use frambuffer.

I'm a little perplexed becaues a driver problem shouldn't quit X to a blank screen, but rather into the text prompt. But I've had driver problems in the past (particually with xfree86) that gave no sign of life but a blank, useless, screen.

---

