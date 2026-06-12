---
title: "raid 0 and ubuntu"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by jeff00z28 on 2007-06-07
I have one logical drive that is on raid 0. I would like to install ubuntu on it. and ditch xp other than in vmware. How would I install the raid driver in ubunu is there an option i never noticed. Thanks

---

### Post by crispy_420 on 2007-06-07
This may be a little complicated and I don't have the specifics but look into LVM. That is basically the RAID setup for linux.

---

### Post by daschmidty on 2007-06-07
Linux and Mobo/BIOS RAID is a dangerous game. However, if you don't want to dual boot, then kernel RAID works just fine. It's basically the same setup except that the array is controlled by system software instead of driver firmware(it's just not readable by windows). Unraid your drives in the bios and then use the ubuntu alternate install cd. Do the manual parititoning. First create about a 100mb parition as ext3 on your first frive, and te3ll the partitioner to mount it as /boot, because GRUB cannot boot a kernel RAID array. Then make a swap somewhere. Then make parititions on each drive and format them as "physical volume for RAID".  Once you have your space allocated it is time to setup the array. Go all the way to the top of the list at the partitioner screena dn there should now be an option to configure software RAID. Go to it, and select create multidisk device. Add all of the "physical RAID volumes" you created and then select OK. The partitioner main screen now should have a new device listed as md0 with free space equal to the total amount you gave the array. Select the free space on the array and change the mounting from "Do not use" to "/" then format it as you wish. AGAIN make sure you make a /boot or the installer will die at GRUB-install and you will get to start all over again. Good luck and feel free to post any questions.

---

### Post by jeff00z28 on 2007-06-07
thanks will do

---

### Post by panto on 2007-06-08
Hi i install ubuntu 7 on xeon RAID O but if i write the dmraid -r i  have this message "No RAID disk ", i use the tutorial on [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug) , and i obtain the file outuput like the tutorial describe but i don't konow where i post this file?? Can someone help me?

---

### Post by Kang on 2007-06-09
> **daschmidty said:**
> Linux and Mobo/BIOS RAID is a dangerous game. However, if you don't want to dual boot, then kernel RAID works just fine. 

Is it possible to dual boot Ubuntu/WinXP if ubuntu is on two SATA RAID0 drives while windows are on a separate IDE drive?

---

### Post by jeff00z28 on 2007-06-10
thanks i dont want to dual boot lol. I'm just gunna install a vmware player w/ xp and another w/ 2003 just for when i rly need a windows applet or something. I've been usin linux regularly for about a month and prefer it over windows

---

