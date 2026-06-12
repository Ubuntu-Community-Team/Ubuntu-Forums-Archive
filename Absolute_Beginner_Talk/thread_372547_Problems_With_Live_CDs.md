---
title: "Problems With Live CDs"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by totalnub on 2007-02-28
I really wish to dual-boot with xp and ubuntu on my laptop. i've been doing a ton of research on the idea. However, I've gotten very close to partitioning my drive with Gparted, and it says i have at least 2 bad sectors. Doing some research, after i did all of the manditory chkdsk /f /r and ntfsresize -b -s 60G /dev/hda1 i get an error having to do with the bad sectors. I found an answer that fits my situation. 

Hello, I had a similar problem with my 120 GB seagate disc which has 4 kb bad sectors.
I could not resize it with gparted-livecd-0.3.3-0 because of the bad sectors. I tried to run some chkdsk /f /r like suggested without luck. The solution was to use qtparted v0.4.5-cvs running from KNOPPIX 5.1.1 live CD. Qtparted ignored the bad sector problem and resized the disc. Running the same version of qtparted from kubuntu 2.6.15.27-386, generates an error when trying to resize.

so now i have dl the KNOPPIX 5.1.1 live CD and i pop it in and when it gets to about the 3rd line where it is looking for cd media, it halts......really frustrating. also the ubuntu installer disk for i386 machines stops on the loading screen progress bar, is this b/c i have an athlon 64? any help would be greatly appreciated.

---

### Post by Kateikyoushi on 2007-02-28
I would agree that your A64 is the reason but not the cpu itself more likely some motherboard component. I do not have an A64 so do not have a first hand experience with this but I would try the following.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by totalnub on 2007-02-28
thanks, will try that when i can, is this for the knoppix or the ubuntu? b/c i know i need to repartition and i don't trust the ubuntu partitioner from what i've read.

---

### Post by Kateikyoushi on 2007-02-28
I think both would need this to boot, migt be your ide controller or sth.

---

### Post by totalnub on 2007-02-28
ok, so i was able to partition my hd into a ntfs 65GB, 6GB ext3, 1gig linux-swap, 24GB ext3, and like about 5gb fat32......so....now i put in the ubuntu install disk, and type live acpi=off and i get this:

```
Cannot open root device "<NULL>" or unknown-block (8,1)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS : unable to mount root fs on unknown-block(8,1)
```

PLEASE HELP!
i really want to install this, but >< both versions i386 and a64 freeze at that same point.

---

