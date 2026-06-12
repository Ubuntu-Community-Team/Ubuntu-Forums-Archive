---
title: "buffer i/o error on device hdd logical block 178868"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by matoot on 2006-12-27
help....i'm completely new to this I tried typing irqpoll after boot:  it said kernal not found or something.  How do I solve this problem step by step for a complete newbie to Ubuntu.  I'm trying this out on an older machine.

Thanks,

Rob

What do I input after "Boot:"

---

### Post by kidders on 2006-12-28
Hi there,

A prompt like "Boot:" sounds like something you'd see while booting your machine, asking for the name of a kernel to load. "irqpoll" apparently isn't the name of an available kernel. Sometimes, depending on your environment, you can hit [Tab] to get a list of available kernels. Other times, a default kernel might load after a short timeout. What were you trying to do by typing "irqpoll"?

> buffer i/o error on device hdd logical block 178868This sounds like something you'd see in a system log, *after* having booted. The only time I've seen such a message is where there is a physical error on a block device (CD, RAM, hard disk, etc.). In the case of hard disks, this can be handled by creating a bad block map with fsck. In the future, your system would then avoid the damaged areas of your disk.

**Edit:** If I'm on the right track with this, you might want to think about replacing your disk, or at least checking it for SMART support. If, over time, the number of bad blocks changes, this can be a sign of impending failure.

---

### Post by warlock_handler on 2007-03-12
Hey i had a similar problem... 
and i figured what was wrong.. there were some bad sectors in the HDD and hence i was getting that error.. so what i did was formatted my HDD and this time while installing uBuntu i selected manually partition your HDD.... i put the root, /home, /urs, /boot, /var etc is different partitions i had made... and it really helped out.. ohh my suggestion whatever be your RAM create a SWAP partition that is atleast twice or three times more of that size..

---

