---
title: "Ubuntu Server Install Fails at Raid Driver..."
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by SydneyStephen on 2007-04-16
Brand new to Linux - and trying to carry out our very first install of Ubuntu Server...

We have a 3-4yr old HP LP2000R server with an HP version of an American Megatrends RAID controller (HP RAID-2M) and we would like to use the drives in a RAID array.

We have downloaded a Linux driver from the HP website - this is a Linux driver set for the correct card but I think it is for the Red Hat distribution.  It generates two floppy disks.  On one of these are what appears to be 2 driver files - megaraid.c and megaraid.h though on the disk they are in an archive file.

At any rate, the installation stops at the discovery of the disks and cannot find an appropriate driver on the floppy disks.

I have read stuff in other posts about compiling drivers and suchlike - but this is way too technical for us...

Is there an easy way to obtain a driver which will work for us, or are we wasting our time trying to get Ubuntu working on this machine?

---

### Post by dozch on 2007-04-16
Don't bother with the drivers you got - you'd have to compile them first anyway...

There is a good Howto on how to setup Ubuntu on RAID array (though I don't think that qualifies as "an easy way"): [FakeRaidHowto]("http://https://help.ubuntu.com/community/FakeRaidHowto")

---

### Post by SydneyStephen on 2007-04-17
The correct link is [https://help.ubuntu.com/community/RaidConfigurationHowto](https://help.ubuntu.com/community/RaidConfigurationHowto)

but i am not sure this will work for us.  the server install cannot get past loading the driver for the controller.  even linux software raid requires a driver for the disk controller no?

Any other suggestions?

---

