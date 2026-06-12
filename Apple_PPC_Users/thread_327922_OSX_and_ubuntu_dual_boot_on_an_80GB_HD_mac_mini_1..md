---
title: "OSX and ubuntu dual boot on an 80GB HD mac mini 1.42"
date: 2006-12-30
forum: Apple PPC Users
---

### Post by ms-das on 2006-12-30
I have the first-generation mac mini, with an 80GB HD, 1.42 PPC G4 CPU, 256MB of RAM, and OSX 10.3.9 "Panther" I was wondering if there is any way to run a dual boot on this system, so that whenever I turn it on, I can choose whether to boot into OSX, or into Ubuntu.
Sorry if this has been previously asked, I couldn't see any stickies regarding this issue. I have already looked for instructional videos for this, but all of them were for Win. XP and Ubuntu. Please help me

Thanks,:)

---

### Post by 3rdalbum on 2006-12-30
Yep, you can dual-boot this system.

Two ways to do it:

1. Back up everything. Erase your hard drive, partition it with one partition for OS X and some "unallocated" space for Ubuntu. Install OS X. Run the Ubuntu installer and tell it to install into the biggest free space. If, when you restart, you find that you can only boot into one operating system, hold down the Option key on startup. You will get a kind of menu that will let you boot any operating system on your machine.

2. Back up everything. Download the Alternate CD for Ubuntu PPC and burn it. Follow these instructions: [http://www.ubuntuforums.org/showthread.php?t=89960&highlight=hfs%2B+journalling]("http://www.ubuntuforums.org/showthread.php?t=89960&highlight=hfs%2B+journalling")
. The instructions work for Ubuntu versions later than Breezy, but you must use the Alternate CD.

---

### Post by handylinux on 2006-12-31
> **3rdalbum said:**
> Back up everything. Erase your hard drive, partition it with one partition for OS X and some "unallocated" space for Ubuntu. Install OS X. Run the Ubuntu installer and tell it to install into the biggest free space. If, when you restart, you find that you can only boot into one operating system, hold down the Option key on startup. You will get a kind of menu that will let you boot any operating system on your machine.
I'm new at this, but the instructions I found here somewhere recommended installing Linux on the **first** partition on a dual-boot Mac system; I had the impression this was required, but on reflection I don't suppose it is. However, it has one great advantage: that you can boot into Linux quickly and simply by pressing the D key during startup, rather than having to go through the tedious option-key routine. See **[ How to switch OS on dual-boot Mac?]("http://www.ubuntuforums.org/showthread.php?t=318682")** for a detailed discussion.

To install Linux on the first partition, rather than leaving some "unallocated" space, you'll need to partition your HD (with Mac OS X Disk Utility from the Install DVD) into two partitions: the first for Linux, the second for Mac OS. Give them distinctive names, so you can tell which partition you want to use for Mac OS X when you install it. (The Linux partition will be erased and un-named when you install Linux anyway.) Then install Mac OS X on the **second** partition. 

I'm afraid I don't remember exactly how I then installed Ubuntu on the first partition; I thought I kept notes, but can't find them now. I believe I started from the Ubuntu CD, then opened the GNOME Partition Editor (under System>Administration) and erased the first partition, which the Ubuntu installer then saw as "free space", and installed Ubuntu on it. (Make sure not to erase your OS X partition, or any of the numerous little Apple driver partitions before it -- which are not visible in the OS X Disk Utility. You can identify the free partition you left for Linux by its size, which you'll recall from when you created it in OS X Disk Utility.) The Ubuntu Live CD installer won't install on a partition created by the OS X Disk Utility, which is in HFS+ format, and it doesn't offer an option to erase only a partition (rather than the whole disk). So you have to give it some unformatted "free space", which can't be created in OS X Disk Utility in the first partition position; thus this workaround method. (Next time I do it -- when I get my 'Pismo' PowerBook G3 up and running -- I'll document the process in detail and post it here.)

When you restart after doing both installations, your Mac should boot into Mac OS X, which was set into firmware when you installed OS X. If it boots into Linux the first time, restart and in the  initial yaboot screen press X to make it boot into OS X. Then open System Preferences: Startup Disk, and select your OS X installation. Thereafter it should boot into OS X by default. Then all you need to do boot into Linux is press the D key during startup, which on New World PowerPC Macs forces the computer to start from the first partition. Then to return to OS X, simply restart without the D key, and it'll boot in the default set in firmware, OS X.

In my case, I decided I wanted to give OS X, which I use most of the time, 32GB of the 40GB HD in my iBook, and put Linux on the remainder. You might think that would be 8GB, but it was more like 5.something, since a "40GB" disk isn't *really* 40GB in size, thanks to hard disk manufacturers' marketing divisions, who count a "gigabyte" as 1000 megabytes, rather than the correct 1024 megabytes. Anyway, to do this required a further step: I first created a 32GB partition and noted the exact size of what was left over (5.xGB), then I erased the disk again and created the first partition at that size; then the second partition (what was left) was 32GB (actually 32.03, I believe, to obtain a formatted size of exactly 32GB -- I like binary numbers). Then I proceeded as above, installed OS X on the 32GB second partition, and used the 5.xGB first partition for the Linux install.

---

