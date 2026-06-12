---
title: "Quick questions before I install Ubuntu"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Native Dialect on 2007-03-11
I am hoping that none of these questions are covered in a thread that I some how missed, so I apologize ahead of time if that is the case, but I did do independent research first. I have the Ubuntu Live CD for the latest version (6.10) and I am aware that I can install ubuntu to a drive entirely,rather than having to constantly boot from the disc. Now I have two HDD's. My main (40GB) has Windows on it, but my slave (80GB) only has movies and television shows on it. My question is, can I intall Ubuntu to my slave drive, without having to partition it? Should i copy my movies and shows to my master drive, before installing ubuntu to the slave drive? Or can I install it to my slave drive, without moving and losing anything? And lastly, when I do install it to my slave drive, do I have to change any boot parameters in my BIOS so that my computer will ask me which drive to boot from, or will that happen automatically after installing Ubuntu?

---

### Post by Kateikyoushi on 2007-03-11
You have to partition the drive, to be able to install ubuntu. Most likely you can install it without a problem the second drive, but do a backup of important data, there is a very small chance of things go wrong but it is there.

Ubuntu will install it's boot loader for you and you can select when you start the PC which OS to boot. Read more about setting up a dualboot system here. [LINK]("http://www.psychocats.net/ubuntu/installing")

Before partitioning run a checkdisk on the drive to see if it is healthy and defragment it few times, also make sure you have least 10GB free space on it.

---

### Post by pveith on 2007-03-11
You need an partition to install Ubuntu 6.10. If you really don't want to repartion your slave drive and non of it partions can be overwritten, then the only solution for installing Ubuntu would be to use feisty fawn (development Ubuntu, will be finished in April). See thread: [http://ubuntuforums.org/showthread.php?t=338279](http://ubuntuforums.org/showthread.php?t=338279)

But keep in mind the install method and the Ubuntu itself are both in-development products. To get a clearer view of this read the mentioned thread.

---

### Post by SurR3AL on 2007-03-11
i'm not sure mate but u should check [this]("http://www.psychocats.net/ubuntu/partitioning/") and [this]("http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu") :)

---

### Post by steve.horsley on 2007-03-11
You have to partition the drive. In fact, you need to create two partitions at least - a large one for the system to go on, and a small one (maybe 1G) as a swap partition (virtual memory for when you run short of RAM). These two partitions have different filesystem types (ext3 and swap) and neither is readable by windows without installing special drivers.

I think the easiest way to install is to use a tool you know and trust to reduce the size of the existing partition (your photos partition in this case) to leave unpartitioned space. Then tell the Ubuntu installer to use the free disk space - it will then create the right types of partitions in that space you made.

**Always** do a full backup first. Same way as you take out medical insurance before driving to the shops. You very likely won't need it, but things can and sometimes do happen.

---

### Post by Native Dialect on 2007-03-11
Okay so let me just make sure I have this all in order. I shoud back up everything on my slave drive, and partiion it, then install Ubuntu. Does Ubuntu have a partion program in it, that I can use, when installing it?

---

### Post by Kateikyoushi on 2007-03-11
Yes the installer has a partitioning program which you can use delete make and resize partitions. I really recommend to check out this installation guide which has pictures to guide you to install a dualboot system. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by mrmonday on 2007-03-11
1)Back up
2)Defragment, run checkdisk
3)Install
Ubuntu has an easy to use partitioner, built in. Just follow he install process.

---

