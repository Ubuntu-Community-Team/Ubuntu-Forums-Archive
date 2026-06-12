---
title: "Booting problem, completely baffled, please help!!"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by mlalich on 2006-09-24
I am trying to install Ubuntu 6.06.1 Desktop on a spare computer. I can get Ubuntu to completely install with the LiveCD version and the alternate version. Once the system reboots it'll get to where it's searching for a bootable drive and it says, "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER". It was suggested to me to use gparted LiveCD as the partitioning portion of the Ubuntu LiveCD might be the problem. So I used gparted and partitioned the only hard drive in the computer as such.

/dev/hda1 ext3 boot flag is on
/dev/hda2 extended
 /dev/hda5 linux-swap

Now I am totally new to Linux so please excuse my probaly idiotic questions. I know standard windows partitioning pretty well, but have no idea how Linux partitioning works. So can anyone please give me a walkthrough, tip, or suggestion on how to get Ubuntu to boot up for me? Oh I did successfully install Ubuntu on VMWare and it works fine, so I know the CDs I'm installing from are fine. I also have tried several hard drives and all same results, so the hard drives are also okay.

Thanks!

---

### Post by bulldog on 2006-09-24
Try to install again I'm afraid,and when it comes to partitoning let ubuntu use your whole hdd and let it figure out by itself how to do it.

It should put GRUB at the beginning of your hdd [MBR] which you need to boot different kermels.

---

### Post by mlalich on 2006-09-24
Well I ran the installation again and had it figure out the partitioning, but still same problem. If the data has been written to the partition now should I need to just jack around with the partition settings to make it mount or something? Any ideas?

---

### Post by MWAAAHAAA on 2006-09-24
Seems like your system cannot find the OS. Are you sure you have the correct boot order set in your BIOS?

---

### Post by mlalich on 2006-09-24
You may be right, but I don't know how to fix it. I have it setup in the BIOS to only boot from the hard drive, the only hard drive in the computer. I have manually partitioned the hard drive via gparted LiveCD and also let Ubuntu Live and alternate CDs automatically configure the partitions. I'm using a Mach Speed P4M800 motherboard if that helps. Has anyone had a problem with this mobo? As there isn't any documentation on the MachSpeed website for this mobos BIOS, I'm lost for ideas. Tonight I ordered an Asus P4V8X-MX to see if it's a mobo/BIOS issue. I've always had better luck with ASUS. I've never used a MachSpeed mobo before, my friend just had this one sitting around new in the box, so I asked if I could use it. I've never had so much trouble with a mobo before!

Ideas and suggested are still appreciated!

---

