---
title: "Ubuntu / Windows XP Slow Dual Boot"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by cawfee on 2007-10-18
Hey all,

following system:

Dual Core AMD Athlon64 X2 5000+ 
2 GB of DDR2-RAM
250GB harddrive
(Dell Inspiron 531)

I recently installed Ubuntu on my system that had run solely on XP before. I used the Ubuntu installer to resize my main NTFS partition (was regularly defragmented and only used about 10 GB anyway), and split the two in half. Each OS now has around 120GB of space available. Ubuntu seems to run just fine with this setup, and Windows retained all settings and configs as well, but I have one issue: Windows load times.

Before installing Ubuntu, the system would boot into XP and be useable in less than 30 seconds. Now, when booting through the GRUB boot manager, it takes around 1 minute to get to the desktop, and another minute to load all startup applications (around 3; one firewall, a defrag manager and the sound driver panel). Games still run fine, it's just the startup speed that's causing headaches.

I have a 4 GB pagefile set in Windows, which I reset and re-allocated to make sure it wasn't corrupted. I also ran another defrag, and a chkdisk in Windows to see if there were corrupted sectors; nothing of the sort.

I read through the other threads that seemed to have similar issues, but it all boiled down to people having tiny hard drives or fragmented partitions, none of which is the case here. Any ideas :confused:

---

### Post by jackflap on 2007-10-18
Never ever heard of this problem before. Sorry, can't help, but then again, you've got Ubuntu.. forget XP! :P

Alex

---

### Post by fallibledragon on 2007-10-18
This is more of a windows issue than an ubuntu issue.  But, try checking your windows event logs and boot logs.  Event logs are in control panel, under administrative tools.

---

### Post by cawfee on 2007-10-18
> **jackflap said:**
> Never ever heard of this problem before. Sorry, can't help, but then again, you've got Ubuntu.. forget XP! :P

And forgetting about XP is exactly the reason I chose a dual boot solution instead of running Ubuntu all on it's own! Horray common sense!

I asked a mod to move this thread, so it should be more appropriate in the newbie area. Will check the logs, thanks C:

---

### Post by cawfee on 2007-10-18
A follow-up to all users who might have the same problem as me:

1) Uninstall all resident antivirus, third-party defrag and firewall software as well as any other hard-drive related product after the partition resize, then reinstall them after a reboot. There's an off chance these programs will try to access parts of the HDD that are no longer available to them and thus cause faults and slowdowns.

2) Defrag with the program of your choice (Ashampoo, O&O etc.) after the repartitioning, but only *after* re-installing your security software.

3) Resize your pagefile, reboot, then set it back to the old value.

4) If you use Nvidia's NForce to manage your network drivers, you need to un-and reinstall them since they will spawn "file not found" errors to no end. A simple reinstall fixes this.

Hope it helps to all who are as puzzled as I was C:

---

