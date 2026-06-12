---
title: "I have an interesting problem and need advice/help"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by masterskop on 2007-05-19
Hi,

My server machine is slowly dying.  The hard drive - 20 gig drive, which is set to IDE 0, has multiple problems.  I bought a new hard drive, which is about 250* gig big and I was thinking about creating a dual boot with that drive.  Probably in the following fashion after reading more postings about it:

partition 1 : windows xp
partition 2: ext3 (share files between windows and Ubuntu)
partition 3: ext3 /home .... (incase of reinstallations of ubuntu or for future ubuntu upgrades)
partition 4: Ubuntu
partition 5: swap


If I set this drive -- 250+  on IDE 0 and made it the master drive and placed the 20 gig "old" drive on IDE 0 and made it the slave, what would I need to do in order to get these drives to:

1. How to  Boot properly in case I have to boot into either drive
2. Copy files from the old drive to the new drive?

This means for this particular setup I'll have two bootable windows xp setups (one old and one new) and ubuntu.   Is this possible? And how would the menu.lst look like in ubuntu?

---

### Post by Najand on 2007-05-19
Yes... 
1. You just need to add the windows partition information to grub's menu.lst. (If it couldn't find the partition and add it to the list automatically)
2. What kind of files do you want to copy?

---

### Post by masterskop on 2007-05-19
Najand,

I have a couple of storage drives w/ programs, games, and files ( word processing, music, pics, etc...) besides the main OS on the 20 gig drive.  I would like to transfer this information over before it's too late.  Also, I would like to copy over the "old" windows' registry and "re-edit" this file, so that I can use the apps and games later...possibly copying them over to the ext3 filing system.  I believe that windows xp can read/write to ext3?  So, there should not be a problem.  Once everything is worked out, the "old" windows' drive will be reformatted if possible and used as pure storage.

---

### Post by Najand on 2007-05-19
Windows cannot read/write EXT3 by default. They don't care about linux in Micro$oft.... But there are tools to use for using EXT3 drives in Windows. Check: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by masterskop on 2007-05-19
ok,

Another question:  If "old" hard drive with windows xp is set from master to slave and the "new" hard drive with ubuntu is set as master or cs, would the following occur in the menu.lst of ubuntu?  Both drives are on the same cable and plugged into EIDE 0.

### END DEBIAN AUTOMAGIC KERNELS LIST

## MY ADDED SCRIPT
## Used to dual boot with Windows XP
title Microsoft Windows XP [Operating System that you know]
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

## End of Windows XP option

---

### Post by Najand on 2007-05-21
Well... If your Windows is on /dev/hdb1 then it should work.

---

