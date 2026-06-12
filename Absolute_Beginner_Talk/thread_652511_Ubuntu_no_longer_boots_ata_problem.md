---
title: "Ubuntu no longer boots: ata problem"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by z3nimagine on 2007-12-28
I installed Ubuntu 7.10 on my laptop with amd64 processor and used it very happily until it stopped loading. If you can help or at least help me diagnose my problem please reply. Here are some details: the last time it worked i was messing around a bit trying to install gta with wine.. no luck. when i tried to shut down the computer afterward it froze up about half way through. after giving it more than enough time i manually shut it down with the power button and now every time i start my pc i get the error message \
ata1.00:  exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
(irq_stat 0x40000001)
cmd 25/00:08:6f:11:98/00:00:11:00:00/e0 tag 0 cdb 0x0 data 4096 in
i tried just reinstalling ubuntu with the cd and it takes me straight to a command line. help please, im lost :(

---

### Post by eternicode on 2007-12-28
Oooh, not good.  The only time I've seen the "Emask 0x0" line was when I was trying to fix what I can only assume is a corrupted hard drive (I'm still working on this drive...and I'm not very hopeful for its recovery :( ).

I would try booting into a live rescue cd (such as [SysRescCD]("http://www.sysresccd.org/Main_Page") or the Ubuntu LiveCD if you already have it) and run a fsck on the partitions from a command line.

Under the rescue environment, if you can mount the faulty partitions and read *some* data off of it, try to backup any important files before running fsck.  You may get I/O errors similar to what you got before, but it should let you read at least some stuff with ls and cp.

Make sure your BIOS boot settings are in the right order.

"fsck.vfat -favw /dev/hda1" for FAT32 partitions (replace /dev/hda1 with the partition to be checked).  Check the man pages for options under fsck.ext2 and fsck.ext3.  I don't think a fsck for ntfs exists yet.

It's possible that you may run into an infinite loop of identical errors (the Emask 0x0 errors).  Just let this run for a while; if you have a verbose switch in the fsck command, fsck should tell you if, when, and what it fixes.  Once these alerts have stopped for some time, and the loop is still going, you may have to Ctrl+C out of the loop.

Also, out of curiosity, which CD are you using to install Ubuntu?  I haven't used the alternate install CD, only the LiveCD, but it doesn't really make sense for either one to boot straight to a prompt.

Let us know how it goes.

Edit:
For future reference, before a hard shutdown, try holding the Alt+PrintScreen buttons down and typing REISUB.  Handy little tip I got from [LifeHacker]("http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php").  Not sure exactly how it works, but the REISU part kills various processes and the final B sends a reboot signal.

---

### Post by z3nimagine on 2008-01-02
I installed that system rescue distro onto a usb pen drive to determine that my hard drive is, in fact, corrupt. Only 2 months old.. thankfully under warranty. thanks a lot for your help.

---

