---
title: "About Extracting ISO to CDR"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by elcapy on 2007-04-19
Hey everyone new to this Ubuntu but loving it now would like to upgrade but need to burn the iso to cd how to i do this i know in XP but Ubuntu i have no ideal what to use or how to go about it i know it will take a maybe two or three cd since i have no DVD burner so if anyone can help please also if you need to know what i use is ubuntu 6.06 LTS ... thanks in advanced

---

### Post by kfrance on 2007-04-19
You can just right click on an iso and click on write to disc.

---

### Post by x64Jimbo on 2007-04-19
GnomeBaker also has the option to burn an ISO to a disc just like Nero

---

### Post by aysiu on 2007-04-19
> **elcapy said:**
> Hey everyone new to this Ubuntu but loving it now would like to upgrade but need to burn the iso to cd how to i do this i know in XP but Ubuntu i have no ideal what to use or how to go about it i know it will take a maybe two or three cd since i have no DVD burner so if anyone can help please also if you need to know what i use is ubuntu 6.06 LTS ... thanks in advanced Well, a few things you should know:

1. Upgrading by skipping releases (Dapper straight to Feisty) will probably result in a broken system.

2. Upgrading the proper way (Dapper to Edgy to Feisty) will take a really long time, even if you have a fast connection, but you don't need a CD to upgrade. You can do it straight over the internet.

3. If you *do* decide to upgrade by CD, make sure to get the Alternate CD. You cannot upgrade using the Desktop CD.

4. Your best bet is to [create a separate /home partition](http://www.psychocats.net/ubuntu/separatehome) and then do a clean reinstall of Feisty.

---

### Post by elcapy on 2007-04-20
Thanks all i think I will just run both for now so until I know that the new 7.4 it's completely good to go with all my hardware. I will keep using dapper then do a clean install of 7.4... well go to get back to play with this System until i learn it well...

---

### Post by x64Jimbo on 2007-04-23
> **aysiu said:**
> 4. Your best bet is to [create a separate /home partition]("http://www.psychocats.net/ubuntu/separatehome") and then do a clean reinstall of Feisty.
The advantage to keeping a separate home partition is that you can do a complete "fresh" install with the Desktop CD and as long as you use the same username as before, don't format the partition, and set it up to mount as the /home directory while you are installing, you won't lose much at all in the way of what you've done to customize the OS. Your firefox profile, OO.o settings, beryl configs, etc will all be saved. I've been using the same home directory on my desktop since Dapper.

---

