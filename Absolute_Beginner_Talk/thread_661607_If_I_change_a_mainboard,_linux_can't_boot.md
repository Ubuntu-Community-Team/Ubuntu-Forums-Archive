---
title: "If I change a mainboard, linux can't boot?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by enjtpl on 2008-01-08
My mainboard broke, so I bought a mainboard. It's same brand, so linux booted, but windows didn't boot. BIOS of the mainboard had some problem, so I change mainboard again. But next mainboard can't boot linux and windows.
If I install other hard disk drive, and install linux to the new HDD, I can use my data in old HDD?

---

### Post by jeffus_il on 2008-01-08
> **enjtpl said:**
> My mainboard broke, so I bought a mainboard. It's same brand, so linux booted, but windows didn't boot. BIOS of the mainboard had some problem, so I change mainboard again. But next mainboard can't boot linux and windows.
If I install other hard disk drive, and install linux to the new HDD, I can use my data in old HDD?

Yes you can mount the old drive and use your data.

Post some information about the boot problem, Waht is displayed on the monitor? Do you have an error, that you can tell us about?

---

### Post by caravel on 2008-01-08
I don't know of any OS that can simply boot and work after a motherboard change, and especially not Windows!  Changing your motherboard is like changing your PC.  Most of the devices in your device manager, probably 80-90% of them, are on your motherboard so unfortunately you really will need to backup your important files, format and reinstall, if to a new drive you can mount the old drive later to retrieve your files.

I usually have my machine partitioned so that I can at least keep the files that were in my /home partition.  If not then it can be a good idea to keep a storage partition.  If you're using windows and Ubuntu in a dual boot config then this storage partition can be FAT32 so that both OS's can read and write to it.

---

### Post by jeffus_il on 2008-01-08
Linux is good at changes to hardware because of the automatic loading of modules at boot. The LiveCD is a good example. Boot a LiveCD and see how much of your hardware it detects.

---

### Post by caravel on 2008-01-08
True enough.  I've had less problems with any Linux distro as regards hardware and drivers than I've had with Windows.  I've never dared change a motherboard though!

---

### Post by methane on 2008-01-11
If you wanted to exchange a motherboard and processor in your machine, would a new install of Gutsy let you keep what's in your home directory?  I've got a new MoBo and processor and will of course back up my data before I reinstall, but I'm wondering if it's possible that my data gets saved.  If not, then I will go ahead and wipe the drive when I re-install.

---

