---
title: "Points about installing Arch alongside Ubuntu"
date: 2011-10-07
forum: Any Other OS
---

### Post by ratcheer on 2011-10-07
I find myself wanting to try Arch for the first time. It seems to be a bit, shall we say, different. I would like to describe my plan for installing it and ask a few questions.

My 1TB system disk already has Natty and Oneiric installed. There is tons of free space. Here is my current partitioning scheme:

```
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): E99E7567-0852-4369-B18D-97797E01C725
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 1795468175 sectors (856.1 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   0700  Linux/Windows data
   2          618496        34172927   16.0 GiB    0700  Linux/Windows data
   3        34174976       101283839   32.0 GiB    0700  Linux/Windows data
   4       101285888       118063103   8.0 GiB     8200  Linux swap
   5              34            2047   1007.0 KiB  EF02  BIOS boot partition
   6       118063104       158063103   19.1 GiB    0700  Linux/Windows data

```Natty is on 2 and 3, Oneiric is on 6, and they share 4 for swap. I thought 1 was /boot, but that is apparently 5 and, right now, I can't remember what partition 1 is. Dern! Thinking about it, I think I had configured 1 as /boot, while 5 is some kind of recovery data partition for the GPT. But, I'm obviously unsure.

So, anyway, I plan to install Arch, thus. 1) Use gdisk to create new root, home, and swap partitions for Arch. 2) Install Arch from CD. 3) Run grub2 under Oneiric to establish bootability of everything. 

Questions: 1) Is my grub2 plan workable? 2) Can Arch share my existing /boot, or should I create another one. Or, do I even need one?

I have already run Arch as a live CD, and I was unable to compile my  wireless LAN driver. So, I have decided to try to install it to disk.  But, I sure don't want to blow up my Ubuntu installations.

Thanks,
Tim

---

### Post by zhogan85 on 2011-10-07
Your grub2 plan should work, sudo update-grub added arch perfectly for me.

And no, you don't need a seperate /boot for Arch. You can actually skip the installing grub part of the arch install, then when you reboot, you'll have to reboot into ubuntu, but updating grub should add arch to your boot menu.

The arch wikis are fantastic/crucial so I suggest reading them thoroughly.

---

### Post by ratcheer on 2011-10-07
Thank you, zhogan85. I guess I'll get started.

Tim

---

### Post by ratcheer on 2011-10-07
Ok, so far everything has worked like a charm. Install completed with no problems, update-grub in Oneiric configured everything, perfectly.

I still cannot compile my Ralink wireless driver, though. Something is missing in /lib/modules. I copied the firmware to /etc/Wireless/RT2860STA, but that is not even the problem.

I'm off to the Arch wiki.

Tim

---

