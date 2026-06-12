---
title: "Would somebody give me exact steps for manual Ubuntu partitioningl with XP?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by charliepotatoes on 2008-04-14
I admit to being thick about Linux & have had my fair share of difficulty with it's learning curve. Still I like it a lot and want to install Ubuntu 7.10 to my 80 GB laptop that has XP on it. I want to dedicate 20-30 GB to Linux.

I tried to manually install with the Ubuntu disk and wound up reformatting my entire hard drive. So I am stumped. Can someone kindly give me simple steps how to do this--or if not, direct me to a good link? 

I've searched here on the Ubuntu forum and other places on the internet for how to co-install, but procedures are described so technically that I can't understand them. I can't imagine how any absolute beginner could. Thanks for any help.

---

### Post by Paqman on 2008-04-14
Try [Psychocats](http://www.psychocats.net/ubuntu/installing) for a good installation guide in non-technobabble.

When you get to [this screen](http://www.psychocats.net/ubuntu/images/installinghardyplus10.png) you can just drag the line between Windows and Ubuntu to decide how much to give each system. Make sure you give Windows and extra 20% or more of free space.

EDIT: Sorry, just noticed you specifically asked for manual partitioning. While not at all necessary, manual partitioning does have the big advantage of allowing you more control over how your system is partitioned and installed. What was it exactly that you wanted to do that required manual partitioning?

---

### Post by tamoneya on 2008-04-14
We are going to start from the beginning:  The first thing you want to do is install XP.  If you install ubuntu first and then XP, xp will mess with the bootloader and then ubuntu wont be able to boot.  When you install xp you should tell it that you want to partition manually.  You want to make a partition that is 50GB (80GB - 30GB = 50GB).  Then proceed with the XP install until XP is fully working.  Then you start with the ubuntu install.  Continue as you did last time until you get to the partitioning section of the install.  Here the easiest way to partition is to say "install on remaining space" or something like that I can't remember the exact wording.  This will install ubuntu into the unformatted section (30GB).  It will also install and correctly configure GRUB so that you can boot either ubuntu or XP at your choosing.

---

### Post by phylwx on 2008-04-14
Hello there, i found this step by step guide to ubuntu studio very useful  [http://phorolinux.com/ubuntu-studio-710-gutsy-gibbon-installation-guide.html](http://phorolinux.com/ubuntu-studio-710-gutsy-gibbon-installation-guide.html)

The other one (psychocats) its very good for Feisty or gusty gibbon :)

Dont give up!

---

### Post by Paqman on 2008-04-14
> **phylwx said:**
> Hello there, i found this step by step guide to ubuntu studio very useful  [http://phorolinux.com/ubuntu-studio-710-gutsy-gibbon-installation-guide.html](http://phorolinux.com/ubuntu-studio-710-gutsy-gibbon-installation-guide.html)

Er, that's actually NOT a good link for someone wanting a dual-boot. Following that guide exactly would wipe your Windows installation. It's also for Ubuntu Studio, not a desktop system and the standard installer.

---

### Post by hyper_ch on 2008-04-14
if you are installing on a blank disk or a to-be-formatted one then start with windows...

during the install process you are being asked where you want to install it. If you read the text there, you can do partitioning. Use all the space you want to windows and leave some free for linux (you said 20-30gb). leave the linux space UNPARTITIONED!

Now go ahead and install windows...

Once done, start with the ubuntu disk and then select, upon partitioning "use largest continuous free space". It will then auto-install into the unpartitioned part of your disk.

---

### Post by Sef on 2008-04-14
For manual partitioning, use the alternate cd, but read the [Illustrated Dual Boo]("http://users.bigpond.net.au/hermanzone/")t first.  It is a little tricky the first time or two, but nothing too difficult with patience.

---

