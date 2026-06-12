---
title: "installing Ubuntu of a SATA hard disk"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by lydmrtnyng on 2006-05-09
Hi i'm trying to dual boot my computer, currently i have successfully installed windows xp x64 on my SATA hard disk; i had it partitioned to 4 logical drive and alloted one partition for ubuntu, while the rest is on NTFS.

my problem is that when i run the ubuntu setup it can't detect the existing partion table i had set, & later on i realized that it didn't really detect my SATA hard disk...

is there a way out here? or may ubuntu can't really support SATA drives? 

thanks! 

:)

---

### Post by uzi09 on 2006-05-09
hmm, not sure about your problem, but i'm running ubuntu and it reads sata hdds perfectly fine. i often mount /dev/sda2 and it works flawlessly.

so yes, ubuntu does support em. i'm curious though, did u leave a partition avail for swap?? cuz u mentioned 4 primary partitions were being used - i read somewhere that ur only allowed to have a max of 4 (although i really don' t think this is the problem here)

---

### Post by nickle on 2006-05-09
It might be that Ubuntu does not recognise your disk controller. Which versuion are you using Breezy or Dapper? Dapper will be more up to date in terms of hardware support.
Check your Device Manager to see if your disk controler is identified.

---

### Post by lydmrtnyng on 2006-05-10
uzi09:so how do i mount my sata hard disk during the ubuntu setup? do you think i should lessen my partition table?

nickle: currently i only had the 4.10 version which i just realized that 5.1 is already out im trying to download it now. 

how long do you think would the version 6 would be out... im thinking if i should wait for the version 6 before i should install my computer with linux.

:) thanks guys

---

### Post by lydmrtnyng on 2006-05-10
:) :) :)

---

### Post by uzi09 on 2006-05-10
[QUOTE=lydmrtnyng]uzi09:so how do i mount my sata hard disk during the ubuntu setup? do you think i should lessen my partition table?

nickle: currently i only had the 4.10 version which i just realized that 5.1 is already out im trying to download it now. 

how long do you think would the version 6 would be out... im thinking if i should wait for the version 6 before i should install my computer with linux.

:) thanks guys[/QUOTE]


i think that may be the problem. linux has no problem booting off a logical partition, while windows (ofcourse) complains...

i'd go ahead and give that a try, change the root partition to be logical.

---

### Post by lydmrtnyng on 2006-05-10
ok i'll try that. :)

---

### Post by nickle on 2006-05-10
If you are doing a new install you should probably try Ubuntu 6.06 (Dapper) straight away. I know it is still a Beta release, but it is already at an advanced stage. I have been using it for over a month and it worked without any problem from a fresh install.
The final version will be available from the 1 June.

---

### Post by steve.horsley on 2006-05-10
[QUOTE=nickle]If you are doing a new install you should probably try Ubuntu 6.06 (Dapper) straight away. I know it is still a Beta release, but it is already at an advanced stage. I have been using it for over a month and it worked without any problem from a fresh install.
The final version will be available from the 1 June.[/QUOTE]

I'll second that. Dapper is shaping up veeeerrrry nicely.

Don't make a partition for Ubuntu. Delete one of the four partitions and leave unused disk space. Then take the installer option to use the unused disk space. It will create 2 partitions for itself (probably inside an extended logical partition) - system (/) and swap.

P.S. Good Luck. And back up first, just in case.

---

