---
title: "Planning to uninstall, &amp; go dual boot.  problem=&quot;Windows recovery cd&quot;"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by raequin on 2007-09-11
I have a laptop with a 40Gb hd.  It has exclusively run Ubuntu all this year.  Football season is motivation to change to dual boot.  That way I can have the TV, and the wife can have a Windows computer.

So . . . the problem is that I don't have a normal Windows installation disk, but a recovery disk.  That's why I'm not looking into VM.  The problem it creates for dual booting, is that it creates a 10Gb partition for recovery stuff or something.  I am assuming that this is unnecessary, as normal Windows installs don't have it.

If the Windows install was a single partition I would just use Partition Magic in the Ubuntu disk.  As it is, I don't know how to procede.  I am guessing that I delete the Linux partitions from terminal with fdisk (a link for that would save me some time searching), then reboot with the Windows recovery disk in.  After Windows installs I guess I would reboot with the LiveCD and use fdisk to delete that 10Gb partition, then hopefully Ubuntu installer would get to play with the entire 40Gb any way it wanted to?  I am also guessing that is not correct.

Please give me instructions for what I need to do to handle this Windows recovery disk.  I hope to split the hd down the middle for the two OSs.  Thanks for your time.

ps - I have been using Dapper Drake, and wonder about moving up to Feisty.  Any comments?

pps - As noted by oilchangeguy, the Windows cd is a factory restore cd.  Thanks, oilchangeguy.

---

### Post by oilchangeguy on 2007-09-11
by recovery disc, i'm guessing you mean a factory restore cd. go to [www.bootdisk.com](www.bootdisk.com) and from there you can create a bootable cd or floppy. if you know how to use fdisk, create a 98 boot floppy/cd. and delete all partitions. and perform a fresh install of windows, then ubuntu. and if you're used to 6.06, and everything works. there's no reason to switch to 7.04.

---

### Post by mikeyphi on 2007-09-11
I don't have any experience of MS recovery discs, but if you know that you can install windows with it - then do that, there should be no need to delete ubuntu - windows will do that! Then use the LiveCD to partition the disk and, as you said, remember to delete the unwanted partition as a first step. 
Yes, consider installing Feisty or if you wait another month, Gutsy!

---

### Post by danny joe ritchie on 2007-09-11
Yes, your recovery disk will remove linux for you!

---

### Post by anewguy on 2007-09-11
Your recovery CD may or may not wipe out the Linux partitions - my Gateway laptop recovery CD doesn't.  If yours doesn't, boot the LiveCD and just run parted to remove any partitions.  You may want to create a 10 gig or so partition for Linux anyway as long as you are in there, that way you can load Windows back from your recovery CD and also reload Linux and dual boot.

BTW - my Gateway recovery disk, even though not a standard Windows disk,  did load in a VM from VMWare Server.   I had to edit the resulting vmx file to change scsi to false otherwise the virtual machine wouldn't boot.

Good luck!:)

---

### Post by danny joe ritchie on 2007-09-11
Wow, I would have thought that all recovery disks give you the option of removing partitions!
Thats a bummer!

---

