---
title: "lost on my new laptop"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by vdub03 on 2007-06-06
ok i just got a dell inspiron 9400 and want to set it up like my hp to dual boot. i'm lost because i have no idea which space i'm supposed to partition. on the hp there was only 2 my recovery and windows. now with my dell i have 4 partitons. and don't know which to use and what to do

---

### Post by aeiah on 2007-06-06
one is windows, one is recovery, one is system tools and the other is some boot diagnostic. something like that. i dont suppose dell gave you the CDs with all this on?

when i tried installing ubuntu on my girlfriend's dell i managed to ruin her pc :p so make sure you read up on the dell partitions. the problem comes from windows not being installed on the first partition on dells, but the 2nd, and it can make things complicated. (i did sort it out in the end, but via a full format and reinstall of just the windows partion and none of the others)

personally i think the cleanest way is to get the dell discs off bit torrent sites (even the dell windows disc if they didnt provide one - you have a license after all), and wipe the hdd. then install windows on the first partition, linux and a fat share on the others etc etc

---

### Post by vdub03 on 2007-06-06
thats what i was thinking of just wiping out the entire system with a clean install and deleteing the recovery partition and using that for my ubuntu. on the other hand if i do this would i void my warrenty with dell

---

### Post by Inxsible on 2007-06-06
Believe me, wiping off the drive is the easiest way to go. HP gave me a recovery partition and I simply nuked it because I knew that the day my Vista goes bonkers, I will simply remove it and give everything to Ubuntu 
:)

---

### Post by Bohlio on 2007-06-06
I have a dell and all i did was shrink the NTFS partition using the live cd and make room for ubuntu, It didnt mess up the system tools or the boot diagnostics partitions. Just shrink the biggest one down and use the free space for Ubuntu and the Swap partition.

---

### Post by vdub03 on 2007-06-06
well problem is i have 2 ntfs files one is huge but the usage is unknown and i can't get into it the partiton it only edit. the other one i'm not to sure of what i'm doing and could use a little help

---

### Post by Bohlio on 2007-06-06
can you post whatever information you are seeing for the rest of us so we can help you figure it out?

---

### Post by vdub03 on 2007-06-06
i sure will give me 15 minutes

---

### Post by vdub03 on 2007-06-06
ok here we go this is what i'm seeing when i goto the partiton setup

/dev/sda                                                         size            used
 /dev/sda fat16 /media/sda1                          57mb            33mb
 /dev/sda2 ntfs /media/sda2                      10737mb       3200mb
 /dev/sda3 ntfs /media/sda3                    147097mb     22500mb
 /dev/sda5 fat32 /media/sda5                      2146mb         842mb


so thats what i see and i'm just not sure which one to use the what size to use and so on so i just need a walkthrough with this info

---

### Post by Bohlio on 2007-06-06
Im guessing that your XP system is the approx. 147 GB one right? Is that how big the C Drive is according to windows? If thats true, then you probably resize your /dev/sda3 drive.

Edit: Going to bed, I'll try and find this thread tomorrow and see if i can continue helping :-)

---

### Post by vdub03 on 2007-06-06
ok and how do i do that i forget, and i'm doing it a different way this time

---

### Post by vdub03 on 2007-06-07
can someone here help me to install ubuntu so i can have it as a daul boot

---

### Post by Tomshaq on 2007-06-07
All you need to do is partition your main windows partition (you may need to defrag first), which appears to be sda3. You can use any partitioning software, such as Gparted. Make sure the new ubuntu partition is just a raw partition with no fs set up. After that, the ubuntu install cd will take care of the rest as far as partitioning, so long as you have a partition with enough empty space.
Good luck and enjoy Ubuntu!

---

### Post by wormser on 2007-06-07
This is just in case you decided to wipe the whole drive and start over.  Dell has a Media Direct option with their laptops.  It lets you boot into a media player only and use it as a CD/DVD player.  One of the partitions has Media Direct on it.  So, if you do go that route and want to use Media Direct do not delete that partition.

---

### Post by Bohlio on 2007-06-07
> **vdub03 said:**
> can someone here help me to install ubuntu so i can have it as a daul boot

Insert the Ubuntu 7.04 CD, Restart your computer, and boot into it by pressing F12 and then selecting your CD drive. This will boot up the Live CD. Then on your desktop click on "Install" It will take you through some steps to configure your language and time and such, then it will bring you into a partition editor. 
You can choose from 3 options.
1. I think this automatically shrinks the First Partition on the First Hard drive and creates the ubuntu / and swap partitions according to a slider that lets you select the % of disk space. I Think thats what the first option does, and in that case you dont want it, since you need to resize your Third partition on your First hard drive.

2. Wipes the whole hard drive and changes it to ubuntu, you dont want this.
3. Three is manual, It will allow you to automatically shrink your Windows partition, then out of the new space, make your "/" and "Swap" partitions. I used this option because I was following a guide. (and ive been trying to hunt down that guide ever since i started posting in this thread... still cant find it. 

Make sure you Defrag as much as possible before doing this.

---

