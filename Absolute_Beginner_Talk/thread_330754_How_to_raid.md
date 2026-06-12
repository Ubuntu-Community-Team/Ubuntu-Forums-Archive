---
title: "How to raid"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by dbbd8 on 2007-01-03
I've set up my ubuntu box with a standard IDE boot disk
and added two SATA disks.

I now want to create a software RAID 1 on those 2 disks.

Most info on building RAIDS either talks about booting, accessing windows partitions, or hardware solutions supporting "software raids".

I'm looking for a bread and butter solution. A device-mapper or an md based setup.
Looking for pointers - what software package(s) do I need, which man pages to read, how to get started.

Thanks,
Dan

---

### Post by kidders on 2007-01-04
Hi there,

mdadm is happy to make software RAID arrays for you. Personally, they're the only kind I tend to use, given all the advantages software implementations have. :-)

Try Googling "mdadm howto", and see if what you need pops up. Be sure and post back if you have any trouble!

---

### Post by dbbd8 on 2007-01-04
Thanks.
I used mdadm to create a raid on my /dev/sd[ab].

I have a problem that it looks like resyncing got stuck after 8% (no more progress)
dmesg has continuous errors like:
```

[42949970.650000] ata1: no sense translation for status: 0x51
[42949970.650000] ata1: translated ATA stat/err 0x51/00 to SCSI SK/ASC/ASCQ 0xb/00/00
[42949970.650000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42950002.050000] ata1: no sense translation for status: 0x51
[42950002.050000] ata1: translated ATA stat/err 0x51/00 to SCSI SK/ASC/ASCQ 0xb/00/00
[42950002.050000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42950107.270000] ata1: no sense translation for status: 0x51
[42950107.270000] ata1: translated ATA stat/err 0x51/00 to SCSI SK/ASC/ASCQ 0xb/00/00
[42950107.270000] ata1: status=0x51 { DriveReady SeekComplete Error }
[42950205.350000] ata1: command 0x25 timeout, stat 0xd8 host_stat 0x61
[42950205.350000] ata1: translated ATA stat/err 0xd8/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[42950205.350000] ata1: status=0xd8 { Busy }
[42950205.350000] sd 0:0:0:0: SCSI error: return code = 0x8000002

```

I tried to partition a small partition (10GB) of /dev/sd[ab] and create a raid1 of these, and again, the same sense errors, and white the building starts fast, it then slows almost to a complete stop.

I do not get any of these errors with dd or sgp_dd on the drives. I found some references to those errors in LKML, but I could not find any resolution

Any ideas?
Dan

---

### Post by dbbd8 on 2007-01-04
Yes, even raiding 10GB failed - it got stuck at 88%.
I'm rebooting and going to find a way to "burn" the drives without raiding first.

Dan

---

### Post by kidders on 2007-01-04
Hey again,

These look like physical problems with your hardware. Here are a few suggestions ... hopefully one of them is the right one! If anything else strikes me, I'll post back.

**1. Physical disk error**
Doubtful, since you mentioned having done disk dumps without problems, but I would still check the surface of my disks, just to rule it out.

**2. Drawing too much power**
During reconstruction of a RAID1 array, both disks are (obviously) churning away quite vigourously at the same time. Your CPU will probably also be quite awake (since you're using a software RAID implementation), and so on. It's possible that your PSU isn't capable of churning out enough wattage to handle the increased load.

**3. Faulty SATA chipset**
Similar issues may have been reported by other users of your specific chipset ... it would be worth checking. (Some chipsets are known to misbehave under high load.) It's vaguely possible that deactivating DMA for your RAID devices might solve your problem. Another possibility might be to split the load over your I/O buses by using one IDE device and one SATA device, for instance.

**Edit:** I forgot to add one important detail ... afaik you can set the maximum data rates for RAID arrays ... try setting a low one, and see what happens. This will help with many possible issues, although you'll obviously take a (possibly large) performance hit, depending on the settings you choose.

---

### Post by dbbd8 on 2007-01-05
Well, I still don't have a solution but had some progress.

I got Seagate disk test tools. I tested each of the disks and they both started to fail at 13/14% with bad sectors

Now these are 2 brand new disks, so I doubt they are really bad.

I then jumpered the disks to 1.5GB interface since they are SATA 2, and my SiL based controller is SATA 1. This got the seagate test suite up to 37% before it starts failing on bad sectors.

So I tried hooking the disks to another motherboard with built-in SATA 1 connectors. Without the SATA 1 jumpers the system couldn't even get to the bios, with it booted to the seagate tools. However, the seagate tools did not even pass the "fast test". 

There goes my trust in SATA equipment compatibility.

I'm going to drop the seagate tools, and try to install and use smartmon on the ubuntu.
However, I have a strong suspicion its a controller-disk issue.

If you have more ideas, I'll appreciate them.

BTW, I'm using an industrial dual feed power supply capable of sustaining 16 hard drives, power is not the problem for sure (on my second box, I had to disconnect 3 hard disks in order to boot with the SATA).

Dan

---

