---
title: "Ubuntu Convert"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-12
After a very shaky start I'm beginning to warm to Ubuntu. One of the biggest problems I had was that my Windows partition was the 3rd primary partition and I was trying to install Ubuntu into partition 2 and Fedora Core into partition 1. Here's what I'd recommend to anyone thinking about installing Linux for the first time:-

1) Make sure that Windows is installed in your first primary partition.

2) Install Linux in a logical (i.e. extended) partition. Make sure your first two logical partitons are Ubuntu and its swap partition. That way, you can add & remove further partitions to your heart's content without upsetting Grub. Most of my problems were caused by constantly needing to uninstall, re-install and re-configure Grub.

3) _Don't_ remove the Ubuntu partition unless you're removing Linux completely!!

4) Ubuntu's version of Grub is better than Fedora's. If you want to try out several different versions of Linux, use Ubuntu's version of Grub.

5) If you want to create partitions using a Windows partition manager, don't use Partition Magic. Use Paragon's Drive Backup. It's miles better.

6) Don't bother trying to mount FAT32 volumes under Ubuntu. Whilst it's nice to have a partition you can share between Windows & Ubuntu, this is still quite flaky under Ubuntu and it ends up causing too many problems.

The only thing I still can't get working is my dual-head graphics card (a Matrox Millennium G400) so I decided to upgrade it. Yesterday I emailed nVidia and asked if they could recommend a card that would give me dual-head output under both Windows & Linux. They emailed me back to say that they don't offer pre-sales advice!!

Therefore if anyone knows of a good, dual-head graphics card that will give 1600x1200 on both monitors under both Windows & Ubuntu, please feel free to recommend it. :neutral:

---

### Post by luvinit on 2006-12-12
Yes, Nvidia are awful if you ask them for help. Unfortunately I can't help you there, but one thing you mention is mounting of drives between Ubuntu and windows. An alternative is cross access via windows using 

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

handy for anyone wanting to copy over documents etc.

---

### Post by John E on 2006-12-12
Thanks for the link. I ended up networking to my laptop as a means of sharing files but it was a bit long winded. Chrysocome's Explore2fs looks very promising!

Incidentally, it mentions being able to read Linux volumes but not write to them. Is that a limitation?

---

### Post by luvinit on 2006-12-12
There is no problem whatsoever writing to the linux drives, it just appears in your "my computer" exactly the same as any other.

---

### Post by Sef on 2006-12-12
> 5) If you want to create partitions using a Windows partition manager, don't use Partition Magic. Use Paragon's Drive Backup. It's miles better.

Partition Magic and Linux often don't get along.  A cheaper alternative to Paragon is [GParted]("http://gparted.sourceforge.net/livecd.php").  It will partition, has never given me a problem, and is available for only $0.00 (Zero dollars and zero cents.)  Donations are cheerfully accepted.

---

### Post by ajgreeny on 2006-12-12
Quote  "If you want to create partitions using a Windows partition manager, don't use Partition Magic. Use Paragon's Drive Backup. It's miles better."

I think the best way to create partitions is to download the iso of gparted liveCD, burn the image to CD and then do everything you want with this.  Much better and, I think, safer than using a windows package.  It can even move partitions on the disk(s) if you need.  A great tool.

---

### Post by seijuro on 2006-12-12
> **John E said:**
> After a very shaky start I'm beginning to warm to Ubuntu.

Welcome to the community!

I run Ubuntu on my laptop so I can't help with the dual-head graphics card however I do know that the twin-view feature of my nvidia that allows me to hook up another monitor or even the tv to my laptop does work under ubuntu so there should be a card out there that provides the features you're looking for under both OS.

If you have any other questions we(the community) can help with don't hesitate to ask.

Cheers.

---

