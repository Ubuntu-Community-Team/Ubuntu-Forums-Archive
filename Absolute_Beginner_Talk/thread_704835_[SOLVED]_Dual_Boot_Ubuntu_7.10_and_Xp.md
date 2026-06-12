---
title: "[SOLVED] Dual Boot Ubuntu 7.10 and Xp"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by adg69 on 2008-02-22
Hi new here and completely new to Linux

I have a PC with XP currently installed, my 320gig HDD is set-up as follows Part. C XP 55gig, Part. D. Data 80gig, Part E 25 gig empty and about 125gig of unallocted free space. This is the only HDD I have on the system.

System is E2140 2 gig ram, XP.

I wish to install Ubuntu in Dual Boot with XP, and I want to put Ubuntu on Part.E which is currently empty. I assume this is possible and easy to do?

I have had brief look/go at the install process (in that I have proceeded to the final step but aborted as it did appear to be going to do what I wanted above), using the guided install process.

I had a look at the manual partition install steps and selected Part. E for the install but keep giving me an error with regard to not having selected something to do with MBR.

Can someone please help me with the process to install Ubuntu as dual boot with XP on my Partition E.

---

### Post by Howler9443 on 2008-02-22
Hi,

The first thing I would do would be to install XP and get it up and running.

You refer to part C, part D, etc. I assume these partitions are already formated, etc.

On thing that may assist you in learning about linux is that there are no, "C" or "D" drives. Basically, harddrives and partitions are associated with directories. This basically gives you the potential for unlimited storage.

That means that you could have a partition with say your MP3 files associated with a /media/music directory. You could have the drive associated with pretty much any directory. Great scalability. :-)

Before getting started I would familiarize myself with how Linux names physical harddrives and names its partitions. That will REALLY help you in determining where you want to install things.

Now back to the task at hand. Once XP is installed, all you have to do is to boot up Ubuntu and let it walk you through the install. You will have to pick a destination drive/partition.  If your drive is a SATA drive the name will be something SDA or if its EIDE, something like HDA

/dev/sda1 denotes the first primary partition of the first SATA drive. My guess is that the partition you want to install Ubuntu on will be something like /dev/sda5 or something. Just be sure to pay close attention to the install screen and you should be good to go.

Good luck!

---

### Post by rapiscan on 2008-02-22
Hello there.  I'm a bit confused as to the exact problem you're having. 

> I have had brief look/go at the install process (in that I have proceeded to the final step but aborted as it did appear to be going to do what I wanted above), using the guided install process.

I had a look at the manual partition install steps and selected Part. E for the install but keep giving me an error with regard to not having selected something to do with MBR.

From the above quote, it sounds like the guided install process was working for you, but there was an error when you used the manual install process.  The guided install process should work fine, as long as you choose the option  to install to the largest free space.  This essentially means installing to the largest unpartitioned space (which, by your description should be the "E" partition").  

If you're trying to troubleshoot the error you're getting with the manual install process, I would recommend posting the exact error message that you're getting so we have a better idea of what's going on.

---

### Post by adg69 on 2008-02-23
Okay I followed your advice and did guided install, but struck a problem, Install froze at 82% "scanning mirror" and left me with nothing to do but reboot.

Now can't boot XP at all and as Ubuntu install was incomplete can't boot that either.

So can only operate PC via Live Cd.

How can I recover this problem?

---

### Post by forestpixie on 2008-02-23
redo the install follow the steps as you did before. When you got to the scanning mirror bit how long did you wait? 

It can take a while to complete that, although last time I installed I disconnected from net when it got there and dealt with the mirror problem afterwards - fairly simple to do.

---

### Post by adg69 on 2008-02-23
Ok second attempt successfull, thanks alot.:)

---

### Post by forestpixie on 2008-02-23
ok that's good then - can you mark thread solved

---

