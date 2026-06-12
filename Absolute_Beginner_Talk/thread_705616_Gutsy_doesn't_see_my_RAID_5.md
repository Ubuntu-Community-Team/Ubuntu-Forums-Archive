---
title: "Gutsy doesn't see my RAID 5"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by fbaerkir on 2008-02-23
I'm trying to dual boot Gutsy and Vista on a RAID 5 array. I installed Vista and partitioned it, but Ubuntu only sees the individual HDS, not the RAID. Anyone know how to work around that? Thanks in advance.

---

### Post by CRCarl on 2008-02-24
My guess is that you are creating your RAID set in a software RAID device. A vast majority of motherboards that support RAID do so in software, so do all RAID cards that cost less than about $250.00.

These cards work by offloading the XOR operations from the CPU to the RAID controller, but count on the OS to create and manage the RAID array. Linux supports some software RAID cards - see [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/")

You would need to do some more research but I don't think that you can dual-boot using software RAID. I ran into the same issue (not trying to dual boot, but I wanted good RAID) and eventually splurged on a "real/hardware" RAID card, the 9550SXU-4LP from 3ware/AMCC. This thing rocks. FAST, FAST, FAST RAID 10 across 4 SATA II drives. Wicked.

---

