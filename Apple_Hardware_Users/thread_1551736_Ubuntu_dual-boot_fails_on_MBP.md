---
title: "Ubuntu dual-boot fails on MBP"
date: 2010-08-12
forum: Apple Hardware Users
---

### Post by crmullin on 2010-08-12
I am having a problem installing Ubuntu 10.04 on my Intel-based MacBook Pro.  I've set aside a partition by booting up with the Ubuntu LiveCD and isolating ~20G in GParted.  So, in OSX (leopard) when I type "diskutil list" into the terminal I get:

0:     GUID_partition_scheme     *186.3 Gi disk0
1:                                 EFI        200.0 Mi disk0s1
2:     Apple_HFS Macintosh HD     146.5 Gi disk0s2
3:     Microsoft Basic Data            19.8 GI  disk0s3

This is what I should expect, right?  I've installed rEFIt and boot with that.  When I boot, I get the option of booting OSX from HD or "Legacy OS from Partition 3".  If I choose Legacy, I'm taken to the GNU GRUB menu, where I can choose from Ubuntu generic, recovery mode, two memtests, and two options to boot into OSX from dev/sda2.  If I choose to boot into Ubuntu, it works until the graphic with "Ubuntu" and the five progress dots underneath, which are already red.  It sits there, and does nothing.
I've tried booting in recovery mode, and after it asks me to login and enter my password (from the command prompt on the bottom) it says that it is unable to cd to /home/chris.  

Does anyone have any idea what this problem might be?  I've tried installing this several times, and this is the farthest I've gotten.

---

### Post by crmullin on 2010-08-12
If it helps, when I look at the partitions in rEFIt, it says that the GPT and MBR are synchronised already.  I've done another install, just to see if that would fix the problem, and it didn't.  
I have the bootloader installed to disk0s3, is this correct?  

Please help!  I want to get ubuntu up and running!

---

### Post by benced on 2010-08-13
model number?

have you checked the wiki?

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by crmullin on 2010-08-13
I figured the problem was in the initial installation, and got it worked out.

Thanks for the link though, I'll check it out.  It is a Macbook4,1.

---

