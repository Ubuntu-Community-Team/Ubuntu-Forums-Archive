---
title: "Small unpartitioned space -I want it back."
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-09-07
Is there a way to get this space back?
My Disk Manager shows the following: 
Partition List: 
Free Space (free space unpartitioned) 6.41 GiB (free space not available)
Partition 2: (/dev/sda2, Windows NTFS, access path: /media/sda2) 103.73 GiB
Partition 1: (/dev/sda1, ext3, access path: /) 10GiB
Swap Partition: (/dev/sda3, Memory Swap) 1GiB
Partition 4: (/dev/sda4, ext3, access path: /home) 111.74GiB

-the first listing (Free Space) is dead/unusable/wasted space. How do I get the 6.41GiB back? What app? what do I tell it to do?

My Sys Specs:
OS:  Ubuntu 6.06/WinXP Pro SP2
CPU: Pentium 4E 3400 MHz (4.25 x 800)
Chipset: Intel Grantsdale i915
BIOS: AMI (09/24/04)
RAM: 1024 MB
Video: RADEON X800 PCIe
Audio: Creative Audigy Platinum
HDD: WD 250G (WDC WD2500JD-22HBB0)

Partitions: 1. 10G ext3 (Ubuntu 6.06)
            2. 104G NTFS (WinXP Pro SP2) 
            3. 1G Swap
            4. 112G ext3 (/home)
Optical: LITE-ON DVDRW SOHW-832S

Optical: SAMSUNG DVD-ROM SD-616E 

Thanks for any help you can provide. I always appreciate your time.

---

### Post by coffeecat on 2006-09-07
Free space not available means it is not partitioned, but you have a problem. You have sda1 through to sda4, which means you have four primary partitions, which is the maximum possible whatever the free space available. To have more than four partitions, one at least must be an extended partition. An extended partition acts as a 'container' for logical partitions.

You have two options: delete one of the partitions in order to be able to create an extended partition with logical ones, or increase the size of one of the exisiting partitions using the unallocated space. But before you do that you need to know where physically the free unavailable space is.

Suggest you boot up with the Ubuntu live CD, go to System > Administration > Gnome Partition Editor (that gives you Gparted) and post back what it shows.

**Edit:** before you do attempt to resize a partition with Gparted, back up everything on it - do a system backup if necessary. Partitioners have been known to crash/fail during partition resizing with the loss of all data.

---

