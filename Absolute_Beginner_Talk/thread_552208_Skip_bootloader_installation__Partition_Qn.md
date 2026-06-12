---
title: "Skip bootloader installation / Partition Qn"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by styfer on 2007-09-16
Hello everyone, wanted to try ubuntu 7.04 and have a few qn (sorry if they are repeats but i cant seem to find the correct keyword to answer my qn...

Current situation:
I have XP and Vista installed, left 40gb free space not partitioned

Qn1) how should i partition these 40gb?
- I have 2gb ram, do i need a swap?
- I dont understand what primary and extended partitions are. For the 40gb of free space, am i suppose to create a primary partition for root and another extended partition for /home? (I know both my window OS uses primary partitions..)

Qn2) how do i skip the bootloader installation?
- since I've installed Vista already, I am using Vista bootloader, however ubuntu is going to intall a bootloader too right?
- I've decided to use the vista bootloader so is there anyway i can skip the bootloader installation in ubuntu ( i can go over to vista and edit its bootloader after installing ubuntu.. )

Thanks all in advance for your help!

---

### Post by por100pre1 on 2007-09-16
Be sure to install GRUB in Ubuntu's partition (click Advanced just before install in the Live CD). That way you can add later Ubuntu to Vista's bootloader easily.

---

### Post by styfer on 2007-09-16
u meant installing GRUB on the root partition?

how about the partition qn? do i need a swap with 2gb ram?

---

