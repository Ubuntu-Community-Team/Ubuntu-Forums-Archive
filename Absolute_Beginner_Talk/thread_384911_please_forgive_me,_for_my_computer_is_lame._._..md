---
title: "please forgive me, for my computer is lame. . ."
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by TheMidnightF0X on 2007-03-15
please forgive me for I'm having troubles installing Ubuntu 6.06.1 on to my notebook pc :
compaq presario 2500
Intel Pentium 4 CPU 2.40 GHz
488 MB Ram (64MB of ram used for video) 
ATI Ration IGP 345M
76 Gig HDD split in to two partitions, 20GB & 56GB

every time i go to boot the cd the first menu will come up, but when i go to "Start or Install Ubuntu" i end up getting the following erroron the top of the screen: "Loading isolinux: Diskerror 80, AX = 4200, drive 9F". and i get this in the middle of the screen "I/O error: Error reading boot CD"

i'm new to linux and would love to give this a try as a good way to break away from the same old same old called windows. Please keep in mind I did follow everything to the letter about downloading and burning it's ISO on to a cd-r. any help in this matter would be highly thanked.

---

### Post by yabbadabbadont on 2007-03-15
Take the option to verify the cd.  Despite your precautions, I would bet that the burn was bad in some way.

---

### Post by TheMidnightF0X on 2007-03-15
> **yabbadabbadont said:**
> Take the option to verify the cd.  Despite your precautions, I would bet that the burn was bad in some way.

once XP's Service pack 2 gets done downloading and installs, i'll do that. however i'm starting to get low on cd-r's i believe that i'm down to 3 left. off hand is it possible to use a cd-rw if i have to reburn the iso once again?

---

### Post by Kateikyoushi on 2007-03-15
Yes, you can use cd-rws I always use that.

---

### Post by TheMidnightF0X on 2007-03-15
thankyou, however one thing i recall seeing was that there was an option to install it from the net. i was wondering is there a floppy disk version of linux i could use to try a web install ubuntu?

---

### Post by Kateikyoushi on 2007-03-15
I found this thread, might still work. [LINK]("http://ubuntuforums.org/showthread.php?t=29358")

---

### Post by TheMidnightF0X on 2007-03-15
> **Kateikyoushi said:**
> I found this thread, might still work. [LINK]("http://ubuntuforums.org/showthread.php?t=29358")
thankyou i'll give this a run.

one of my main goals for wanting to use linux is to get a lil more out of my system. i'm tired of windows XP hogging the memery for it's self. and the video lag i get because XP is having to run so much in the background even following Black Vipers list i still get odd ball problems with it slowing down or acting funny when it shouldn't. hell if this helps me get back to 60fps on CS i'll be happy. as of lately i've been steming out in to a lot of the opensource software (IE: firefox, open office, ect. ) and i love it for the most part.


NOTE: the disket failed, i get the error "Boot Failed" a part of me is starting to wonder if my notebook is trying to fight this?

---

### Post by TheMidnightF0X on 2007-03-15
sorry about that after i had to reboot XP claimed it had another 81 updates.... this is what i'm trying to get away from. i love to call it update hell. but i had a question, does the file format matter much? the HDD partitions are in ntfs. is this going to be a problem?

currently i found this page: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) and so far it has a lot of info reguarding alturnatives for installing ubun.

Note: i just tried to check the cd for defects and got the same error as before. "Error reading Boot cd"

---

### Post by hyper_ch on 2007-03-15
Linux also has a lot of updates...

Before you install ubuntu do:

(1) BACKUP YOUR DATA

(2) Run defragementation at least 2x

[ (3) You may even consider repartitioning/resize your ntfs drive with partition magic if you happen to own it to free diskspace...]

Once that is done, then you can go ahead installing ubuntu. During the install process it will ask you how/where to install it. If you haven't resized your windows partition yet then you will need to select manual partitioning and resize your ntfs partition so that space will be freed (unallocated) where you than can install ubuntu.
With regard to partitions and planing you may want to have a read [here]("http://www.psychocats.net/ubuntu/partitioning").

---

### Post by Aliarse on 2007-03-15
Re-burn the iso, this time, do it at a REALLY slow speed. Something like 2 or 4x.

When i first burned an ubuntu iso at normal speed, the install wouldnt get 1/4 of the way through without giving me errors/hanging, burning it at a slow speed solved this for me.

---

### Post by TheMidnightF0X on 2007-03-15
> **hyper_ch said:**
> Linux also has a lot of updates...

Before you install ubuntu do:

(1) BACKUP YOUR DATA

(2) Run defragementation at least 2x

[ (3) You may even consider repartitioning/resize your ntfs drive with partition magic if you happen to own it to free diskspace...]

Once that is done, then you can go ahead installing ubuntu. During the install process it will ask you how/where to install it. If you haven't resized your windows partition yet then you will need to select manual partitioning and resize your ntfs partition so that space will be freed (unallocated) where you than can install ubuntu.
With regard to partitions and planing you may want to have a read [here]("http://www.psychocats.net/ubuntu/partitioning").

once again thanks for the continuing help. one thing i should have stated in the begining was that i'm doing all of this on a fresh formatting of the HDD. I split the drive in to 2 partitions both with the NTFS file system. as far as i know i'm finally done doing all the updates for XP thank god... 

Aliarse i'll try that. and i'll get back to you once it's done.

---

### Post by hyper_ch on 2007-03-15
You have two partitions each formatted with NTFS?
If so, then delete the partition that you "created for linux". By default linux can only read ntfs partitions.

When you start then setting up the partitions I would advice following setup (also dependant on the diskspace you have)

- SWAP partition (about 2x the size of your ram) use as filesystem "SWAP"
- root partition [-->  "/"]: give it about 7-10gb. On there come temporary data, system logs, program files, ....... 7-10gb should be fine, if you have plenty of diskspace you can add more... I have set mine to 15 GB (but I have a 160GB, 320GB and 500GB disk). Use as filesystem "EXT3"
- home partition [--> "/home]: make this as big as you can as it will then contain the user data. It's sort of the equivalent of "c:\documents and settings" but much more advanced by design :)

What I wrote in those [--> "..."] brackets is the mounting point that you have to assign to the partitions.
Linux starts all with "/" and has not diskdrives like windows. However you just say sort of "add partition xxx to location "/path/to/location" and the content of that partition will then be available there.

---

### Post by TheMidnightF0X on 2007-03-15
this could be the root of thy headache. i'll go in and remove the second partition. 
the thing is on the first partition of 20 gigs i have XP installed the rest was for the linux. i guess my next question would be can windows read from the partition that linux is on? or i should say will the partitions be compatible with one another?

ok i burned the cd at 1X and still got the error. i'm using this ISO. "ubuntu-6.06.1-desktop-i386.iso"

---

### Post by hyper_ch on 2007-03-15
What error do you get?

Well, Ubuntu can natively read NTFS partitions (however not write to them... you will have to get an additional driver that can do it... however I would be carefull about it. If there is a glitch you can loose all your data on the ntfs drive).
There are Ext2/3 drivers for Windows. They are safe to implement and work fine (however those drives can't make use of the journaling...) so you can read/write to ext3.
The third option you have is making a fat32 partition. Both linux and windows can read/write it but it has its limitations (like 2gb file size limit).

---

### Post by TheMidnightF0X on 2007-03-15
well i have no problem formatting to fat32, it's just that with the partition being 64.5 (according to XP) wouldn't it tech. reject fat32 because of it's size? or am i looking at another night of update hell?

eather which way i have to call it a night. i'd like to thank the lot of you for your quite speedy replies to my questions. i'll have to pick back up on in a few hours. thank god i'm on spring break.

---

### Post by hyper_ch on 2007-03-15
Well, I meant to create an additional partition that you can use for exchange data...

---

