---
title: "Dual boot clarification"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Hospadar on 2008-02-17
I'm going to be setting up dual boot on a laptop with one hardrive soon, and I just want to clarify exactly how I'm going to go about it as I've only before set up dual boot on 2-hard drive systems.

Partition setup (160 gb drive):
I want to give windows most of the drive (games, etc), so I'm probably going to take out 145-150gb for windows, then maybe 3-4Gb for "/" and the rest of the drive for "/home"

I'm thinking to first install windows (I'm going to wipe the factory installation completely) on an appropriately sized partition, leaving the rest of the drive for free space.  I assume this will put the windows boot loader in the drive's mbr.

Then I will install ubunto into the remaining free space.  This is where my uncertainty comes in, will grub by default install into the mbr, overwriting windows (ntldr) and if so, can I then do a "fixmbr" with a windows CD to get everything working?  Also, should I (can I) tell either windows or ubuntu to put their boot loaders on their own partition instead of in the mbr?

Thanks for the help!

Luke

---

### Post by sb12 on 2008-02-17
> **Hospadar said:**
> I'm going to be setting up dual boot on a laptop with one hardrive soon, and I just want to clarify exactly how I'm going to go about it as I've only before set up dual boot on 2-hard drive systems.

Partition setup (160 gb drive):
I want to give windows most of the drive (games, etc), so I'm probably going to take out 145-150gb for windows, then maybe 3-4Gb for "/" and the rest of the drive for "/home"

I'm thinking to first install windows (I'm going to wipe the factory installation completely) on an appropriately sized partition, leaving the rest of the drive for free space.  I assume this will put the windows boot loader in the drive's mbr.

Then I will install ubunto into the remaining free space.  This is where my uncertainty comes in, will grub by default install into the mbr, overwriting windows (ntldr) and if so, can I then do a "fixmbr" with a windows CD to get everything working?  Also, should I (can I) tell either windows or ubuntu to put their boot loaders on their own partition instead of in the mbr?

Thanks for the help!

Luke

using grub will still let you boot into windows, why even bother with ntldr

---

### Post by jan quark on 2008-02-17
here is a nice site dealing with dual booting

perhaps it will help you

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by louieb on 2008-02-17
> ... will grub by default install into the mbr, overwriting windows (ntldr)...By default any operating system  will  place its **IPL** (initial program load) code in the MBR. So by default last one installed has its code in the MBR.

> ..and if so, can I then do a "fixmbr" with a windows CD to get everything working?..Lots of ways to put whatever IPL code in the MBR.   Running fixmbr will make it run ntldr. Heres a good list of ways to change the MBR. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

> ..Also, should I (can I) tell either windows or ubuntu to put their boot loaders on their own partition instead of in the mbr?...Windows - don't know of anyway to prevent windows from placing its code in the MBR.
Linux including Ubuntu - flexible install options can place the the GRUB IPL code in MBR or boot sector of its / (root) partition.

Just my [IMG]http://louboldt.com/ptwocents.gif[/IMG] Install windows then install Ubuntu. Thats the easy way to set up a single drive to dual boot.

---

### Post by coolen on 2008-02-18
Grub will install to the MBR. You can prevent it from the Ubuntu installer.

This would be appropriate if you only want to access Ubuntu from a boot disc. However, Grub can boot both Windows and Ubuntu.

Dual booting has never been an issue for me. The installer correctly identifies my Windows installation, and it just works.

---

