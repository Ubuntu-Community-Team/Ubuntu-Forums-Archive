---
title: "Disk Utility &quot;Lost Connection&quot;"
date: 2009-05-15
forum: Apple Hardware Users
---

### Post by jackbusch on 2009-05-15
Hello
I'm running OS X 10.4 and Jaunty. I also had a partition that I was using just to keep files. I wanted to re-format this partition to something that both OS X and Linux could read/write without mucking things up. However, Disk Utility in OS X is giving me the "Disk Utility Has Lost connection with Disk Management tool" error.

I have tried deleting my iTunes receipts.
I have tried running Disk Utility from the Install disc.

My big questions are:

If I simply re-format the partition in Gparted, is OS X going to have issues with that?

Is my hard drive damaged? Should I re-format? Or buy a new hard drive?

I'd like to note that my hard drive failed recently and I had it replaced under warranty. Is it possible that something in my computer is wrecking my hard drive? Or the way I am using it?

Thanks

---

### Post by tiresia on 2009-05-15
Could you please tell something more about your mac?

---

### Post by jackbusch on 2009-05-15
Sure - its a macbook 2,1. I upgraded the RAM with something I bought off of Frys that was advertised as mac compatible. I also upgraded with a Samsung 320gb hard disk that was advertised as Apple compatible.

I'm running OS X 10.4

---

### Post by jackbusch on 2009-05-15
as a preemptive follow up question in case of nuking: What's the best way to triple boot os x, ubuntu and Windows 7 on a macbook from scratch? I've found a lot of tutorials but no real consensus on what's the best.

Note that right now I'm not trying to run Windows 7...but if I'm going to start over I may as well

---

### Post by WA_Garrett on 2009-05-15
When I was setting up triple booting on my mac I had that whole disk utility error a couple of times to. I can't remember exactly what I did to fix it because I think the problem sort of solved its self in a way. I had people tell me to put in the OS X disk and open up disk utility and fix disk permissions and such, but that didn't do anything. I can't tell you why disk utility behaves like this but I think if everything on the disk is just not right, disk utility spazes. 

Considering how I had this problem to, I don't think your Hard Drive is damaged or needs to be replaced.

I dug up an old post I made a few months ago where I got help regarding the same problem. 
[http://ubuntuforums.org/showthread.php?t=1039410]("http://ubuntuforums.org/showthread.php?t=1039410") 
It might be helpful. 
Apparently I had some unpartitioned space on my drive that I freed up using an XP install disk. Unfortunately disk utilities didn't like that. But when I made the free space MS-DOS formated space with Disk Utilities booted from the CD, Disk Utilities no longer reported the error.

---

### Post by jackbusch on 2009-05-16
Great - thanks, actually, that makes a lot of sense. I do have some free space on my hard drive which is probably the source of the problem. I'll see if formatting that fixes the problem.

---

### Post by jackbusch on 2009-05-16
It worked! I just formatted all the free space on GParted and now Disk Utility stopped its bellyachin'. Everything's good. Thanks!

---

### Post by cyberdork33 on 2009-05-16
This is THE documentation for installing on intel mac hardware. If something is not correct there, please refine it.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

