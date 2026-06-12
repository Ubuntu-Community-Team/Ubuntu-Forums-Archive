---
title: "Partition trouble"
date: 2011-03-04
forum: Apple Hardware Users
---

### Post by ftbtef on 2011-03-04
Hi, I recently installed Ubuntu 10.04 on my 2004 iMac. When installing it, I created a bunch of extra partitions, and I'm pretty sure I don't need some of them. I have a 210mb "EFI system partiton", which I think is rEFIt and I believe I need, a 216 gb Apple HFS+, which is my Mac OS X partition, 1gb "Linux Swap Partition", 1mb "Unknown/Bios Boot Partition", 32gb ext4, which is Ubuntu of course, and a 1.4 gb swap space. I think I can delete the 1gb swap, and the unknown boot partition. Is this correct, or are those necessary for Ubuntu?

---

### Post by Colin Rovis on 2011-03-04
Hi, I would recommend not to delete these partitions! 

Linux does make use of the swap partition, and you do not really miss the other partition (it's to small). 

If your system is working, do not change anything, because your iMac can act very angry ;-)

ss
Colin

---

### Post by ftbtef on 2011-03-04
Alright, sounds like a plan. I have one other question, which is I realized I'll be using Ubuntu more than OS X. I'd like to resize the Ubuntu partition from 32 to around 70. Is there a way to do this without erasing the current install of Ubuntu? I haven't done too much, so a repartition and install works for me. But a different solution would be nice...

---

### Post by srs5694 on 2011-03-04
If you're positive your iMac is from 2004, then it uses a PowerPC CPU, not an Intel CPU. As such, it also uses (or *should* use) the Apple Partition Map (APM) partitioning system. The EFI System Partition and the BIOS Boot Partition are both partition types on the GUID Partition Table (GPT) partitioning system. Thus, if your statement that the computer is from 2004 is correct, you've got the wrong partitioning system on the computer, and it probably won't boot at all. If you can currently boot OS X on the computer, then chances are it's actually newer than a 2004 model. If not, then you've got the wrong partition table and you need to start over again, creating an APM partition table using an OS X installation disc, an Ubuntu installation disc, or some other tool. It's hard to give more precise details without more information, such as what OS(es) are currently installed and what OS(es) you're tring to install.

---

### Post by ftbtef on 2011-03-04
I just looked it up, and I have an iMac g5, which used PPC processors. So I'll delete all the extra partitions from Ubuntu, and change the partition. Some questions:

If it's booting (its booted perfectly at least 5 times so far), do I really need to worry?

When I redo the partitions, can I just resize the old partition once its clean, or do I need to make it part of the OS X partition again, then partition with Boot Camp?

I changed some settings so rEFIt defaults to Ubuntu after 15 seconds of startup, will it get "confused" if I reinstall?

Hmm, I still feel pretty sure it's Intel.

---

### Post by ftbtef on 2011-03-04
Nope I've got an Intel processor. But I'm going to redo stuff anyway for a bigger partition.

---

