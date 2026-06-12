---
title: "How to divide my hard drive"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by pastorjay on 2006-10-29
Ok, I am a total Ubuntu/Linux noob.... there, I said it!

I am wanting to dual boot with Vista/XP. ( I have Vista installed atm).  My Laptop HDD is 60Gb, and as of now, Vista and all my apps are taking up about 20GB, leaving me  40 to deal with.  How would you divide the drive up?  And should I use my ubuntu install to partition the drive or Vista? 

As a side note, I have a broadcom wireless device in the laptop, will it work right after install, or will I need to find a driver?

Thanks for you help!

Jason

here are my system specs:

Dell 1705
Nvidia 7900GS
2GB ram
60GB HDD
Broadcom wireless

---

### Post by doctorberen on 2006-10-29
Hello.

If I were you, I would partition my drive as follows:
Partition 1: (NTFS) 25GB Vista
Partition 2: (ext3) 10GB '/' or root partition for Ubuntu Program Files
Partition 3: (ext3) 23GB '/home' partition for your personal files in Linux
Partition 4: (swap) 2GB 'swap" partition

One of the great things in Linux is that if you keep your personal files in a separate home partition, you can play around with different distros and reformat the '/' partition multiple times but still have your personal files untouched. The best thing with this is that your personal configurations are also stored in the separate '/home' partition so they are saved, even after changing distros.

A separate swap partition is also important to keep your system running smoothly.

Be careful when operating the partitioner specially if this is your first time doing it. You can very well accidentally wipe our your Vista partition. 

**I would strongly suggest you backup your data files before undertaking this task.** Seriously man. Back up your windows data first.

---

### Post by tonyr on 2006-10-29
[Here]("http://www.psychocats.net/ubuntu/partitioning") is **aysiu**'s good overview of partition planning.

---

### Post by pastorjay on 2006-10-29
thanks guys!  I already have used Acronis to back up everything, so I am good to go there.  So the swap only needs to be 2GB then, that is cool!  

Now, how about that broadcom wireless card?

---

