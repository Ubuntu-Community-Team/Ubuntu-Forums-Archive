---
title: "Installing 12.04 on a Firewire LaCie 250Gb Rugged with a MacBook Pro"
date: 2012-06-17
forum: Apple Hardware Users
---

### Post by mart21472 on 2012-06-17
My Situation is:

I've tried installing ubuntu many times and my attempts have all been futile. I'm trying to install 32-Bit Ubuntu 12.04 Onto an external Firewire LaCie Rugged 250Gb Hard Drive so I can dual boot it when it's plugged in with the alt/option key, This unfortunately has not worked very well. Every time I've installed Ubuntu on the Hard drive, I try the dual boot option and I get "No bootable device insert boot disk and press any key" Which I have tried replugging the hard drive in at this step but to no avail. I am wondering what are the steps I can take to stop this problem, or if this is even possible to dual boot with. The specs are:

Macbook Pro:
Hard drive is a Toshiba 250gb
Version 10.6.8
Processor 2.53 GHz Intel Core 2 Duo
Memory 4GB 1067 MHz DDR3

Hard Drive:
LaCie Rugged 250Gb External Hard drive connected via Firewire and with my current installing method in disk utility it shows 

Disk1s1, Disk1s3, 4 and 5 and Linux Swap.

Before Reinstalling a friend told me that the ideal partitioning manually would be:

2Mb BIOS Reserve Space
2048Mb Swap area
16384Mb Disk Space
And two other partitions of 16Gb for two other ubuntu boots.

I've tried these also but the same problem of the No bootable device error still appears, I apologize if I have mentioned a topic that's already been discussed, but could somebody please link me to the topic if it has already.

My question in short is:
Now that my external hd has Ubuntu Installed, how do I run it with dual-boot?

---

### Post by maximini on 2012-07-13
Hi mart21472,

I am trying to fix that for FreeBSD on a Mini 2011 and just posted on their forums to that end (see [http://forums.freebsd.org/showthread.php?t=33297](http://forums.freebsd.org/showthread.php?t=33297)).  While looking for hints, I found the following link, which should help you a lot: [http://www.crystalorb.net/mikem/linux_mbp_external.html](http://www.crystalorb.net/mikem/linux_mbp_external.html).  While there are no step-by-step instructions there, it comes close and hopefully either you can figure it out (and if so post what you did), or a good soul can help.

Cheers,
Maximini

---

