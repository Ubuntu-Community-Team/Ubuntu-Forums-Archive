---
title: "how to install xp  and ubuntu in a machine with vista?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by bibas on 2008-03-08
hi,
I want to install Xp and Ubuntu on my compaq laptop.
I ve heard i have to install XP first then install ubuntu.

I tried to instal XP but it says there is no hard drive in my laptop.
Ubuntu shows the hard drive but displays no partition only a single unpartitioned space...doesnt show my laptop's recovery partition.

Ideally i would want the recovery partition undisturbed, with XP and Ubuntu installed. 
But i would settle for just XP and ubuntu installed...ready to sacrifice any other partition. I ve backed up everything on to a DVD.


Thanks in advance

---

### Post by Sef on 2008-03-08
Have you used Vista's partitioner to shrink the partition?   With Vista, you have to shrink it that way.

> I want to install Xp and Ubuntu on my compaq laptop.
I ve heard i have to install XP first then install ubuntu.


That is correct.

---

### Post by bibas on 2008-03-08
Yes, I shrink c: drive and made it 40 GB and created 2 partitions 40(for ubuntu) and 60(for XP)

---

### Post by bibas on 2008-03-08
anybody please suggest me next steps

---

### Post by ianhaycox on 2008-03-08
Long shot, but, The XP install might not be able to see your hard drives if they are not IDE without extra drivers installed during the XP setup process.

If they are SATA drives I have used an option in the BIOS to 'fake' the SATA drives to be IDE so XP can see the disks. Can't remember the option tho' Poke around in the BIOS.

Ian.

---

### Post by uberlube on 2008-03-08
Try setting the NTFS partition to boot.

---

### Post by louieb on 2008-03-08
There are many ways to run vista, xp and Ubuntu on the same pc.
 
Triple boot - each OS in its own partition and some boot loader to allow you to choose which OS to run. 
 
Single boot 1 OS and run the other two in a virtual  machine. 
 
Dual boot Vista and XP, then do a WUBI install of Ubuntu in XP or Vista.  
 
probably a few more that I have thought of.
 
Decide which way you want to go and then help in getting there will be easier.

---

