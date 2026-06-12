---
title: "emac 350"
date: 2007-02-24
forum: Apple PPC Users
---

### Post by ERSchrager on 2007-02-24
Greetings Mac users.  Came across some inexpensive emac's.  But I don't know what I am looking at.

Here are the specs.
# 350 MHz PowerPC 750 G3 processor (CPU)
# 100 MHz Front Side Bus
# 64 MB RAM, expandable to 1,024 MB using two PC100 168-pin SDRAM DIMMs (3.3 V, 64-bit, 168-pin, 100 MHz)
# Video controller supports resolutions of 640 x 480 at 117 Hz, 800 x 600 at 95 Hz, and 1024 x 768 at 75 Hz using ATI Rage Pro 128 chip set
# 15" Built-in Monitor (13.8" viewable) Multiscan to 1024 x 768
# 512 KB backside cache running at 160 MHz
# 30 GB Ultra ATA Hard Drive
# CD drive
# Ready to accept AirPort card (not compatible with Airport Extreme cards)
# Built-in 10/100 Ethernet
# Integrated 56 kbps modem supports v.90 standard
# Fanless convection cooling for ultra-quiet operation

# I/O Ports: 
# Two (2) Separate USB 1.1 Ports and Controllers
# Two (2) 6-pin FireWire 400 Ports
# One (1) RJ-45 10/100Base-T Ethernet Connector
# One (1) RJ-11 modem connector
# Internal microphone
# One (1) Stereo Speaker Minij

It is my understanding that an Apple 350 is + to an Intel 700.  Is this true?

I would like to purchase a couple of these to learn MAC OS(9), and also to try one as a Remote Diskless machine under Ubuntu running off of an Intel server.   Is this possible?

TIA
Roger

P.S.  I also assume i would have to increase the amount of ram.

---

### Post by ERSchrager on 2007-02-24
Follow-up question.

Will Ubuntu run on a imac G3?

---

### Post by 3rdalbum on 2007-02-24
> **ERSchrager said:**
> Follow-up question.

Will Ubuntu run on a imac G3?

Yes, definately.

A 350MHz G3 chip in an Apple configuration is probably similar in speed to a 600MHz P3. Mac OS 9 is also a very fast operating system, so you'll see extra benefits there.

You will need to upgrade the memory to at least 128 megabytes for Xubuntu, or more like 256 megabytes for Ubuntu.

Also, be aware that you cannot resize HFS partitions without OS X, and OS X ain't gonna run on that thing :-) Does the computer come with a Mac OS 9 system install disc? In order to install Ubuntu onto the internal hard drive in a dual-boot configuration, you need to reformat the hard drive, create an HFS partition for the Mac OS, and leave unallocated space for Ubuntu.

Either that, or buy a Firewire hard disk to install Ubuntu onto. Just check first that the Mac supports booting from Firewire.

---

