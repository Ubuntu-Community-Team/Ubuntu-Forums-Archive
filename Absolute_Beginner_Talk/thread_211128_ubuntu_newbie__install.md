---
title: "ubuntu newbie / install"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by wylien on 2006-07-07
hello everyone in the ubuntu community. 
i am a newbie ... a little about me and my computer education. i started using macs in school back in early 90s, later had to switch to pc's (but never really liked having to switch to windows) and became quite comfortable with windows. about a year ago, i decided to finally go back to macs, i bought myslef an ibook and i was very pleased with the change. i still kept my pc (windows) and i have been debating whether to sell it or keep it and learn linux. yesterday i came across an article that mentioned ubuntu and i got very interested.

needless to say, all day today i have been reading, reading and doing more reading about linux and ubuntu. i have decided i want to install ubuntu on my pc and give it a try.

i started by backing up everything that i want to keep and it is finally all backed up.

so far, i understand i can run a test version of ubuntu and check it out. do i need to d/l ubuntu 6.06 in order to run this test version?

i just finished d/l ubuntu 6.06 (32-bit) to my pc and i am unclear on how to verify the file and how to burn the iso to a cd from my windows based pc ... once i have verified the file should i select joliet, iso1 or iso2 to burn it to cd?

next: 
i would like  to format my internal 100gb hd and install windows xp in one partition and ubuntu in another ... 
but:
- i am confused as to the number of partitions i should divide my hd into and the sizes i should give each. 
- does it matter what OS i intall first?

...up to a few moments ago, i was determined to format my whole hd, now i am not so sure if i should -even though i know i need to do so soon because of all the mess my hd is in at this point.

anybody have some few pointers in the right direction?

---

### Post by catlett on 2006-07-07
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) This how to was created by Aysiu (if you stay around you will not be able to miss Aysiu's posts and help) It is exactly what your looking for.

---

### Post by mscman on 2006-07-07
To burn the .iso image file, use a program such as Nero, or if you're looking for freeware, DeepBurner is a great program too.

Once that's done, you'll probably want to reinstall Windows if you're planning to do so. Windows should be installed first if this is your first time, since the Windows bootloader will overwrite the MBR. Once you get more Linux experience, you'll learn that you can install GRUB after a Windows install to keep your Linux partition.

You only technically need 2 partitions to install both OSes: one for Windows, one for Linux.  However, if you want to share data between the two, you'll be best off creating three partitions: one for Windows (ntfs), one for Linux (ext3 -- let the Ubuntu installer format this partition), and one for shared data (preferably fat32). This is due to the lack of stable NTFS support for Linux.

Ask any more questions if you have 'em! And have fun!!!  :)

---

### Post by Sonofmoog on 2006-07-07
> **catlett said:**
> [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) 

One of the best tutorials I've ever read.  I train / teach for a living, and I don't have to be an expert in Linux to recognize good work when I see it.

Highly recommended ..

---

### Post by reacocard on 2006-07-07
the "test" you're talking about is called a livecd, and is included in the download if you got the "Desktop" ubuntu cd. just pop it in, reboot and a fully operational ubuntu will boot. this is an excellent way to test wheter ubuntu will work with your hardware, and to see wheter you like ubuntu (keep in mind the livecd is slower than a standard install). for burning the iso, i'd use deepburner free: [http://www.deepburner.com/download/DeepBurner1.exe](http://www.deepburner.com/download/DeepBurner1.exe) it's free and damn easy to use. just put in a blank cd, point it to the iso and relax.

for partitioning, i'd recommend something like this:

windows (for windows, obviously) - ntfs - 20 GB
/ (root filesystem, main ubuntu stuff goes here) - ext3 - 20 GB
swap (linux's virtual memory) - linux-swap - 1 to 2 times your RAM
shared (for sharing files between XP and ubuntu) - fat32 - 60 GB

ntfs, ext3, and fat32 are the filesystems to use for each partition. create these partitions from the ubuntu livecd (under System -> Administration -> gparted), then install XP, and finally install ubuntu.

Installing XP first is a good idea, since it'll overwrite GRUB if you install ubuntu first, and then you won't be able to boot into ubuntu easily. And yeah format the whhole thing. it's just easier that way.

---

### Post by wylien on 2006-07-07
hey everyone, thanks for the quick responses!

so first, i will check out the tutorial.
second, thanks mscman - oi will go ahead and d/l deepBurner free and correct me if i am wrong. the file d/loads in .rar format which i have to open and add all the files and folders to deepBurner and burn the copy as a bootable iso to a cd, correct?

---

### Post by fhqwhgads on 2006-07-07
Nope, it's an ISO, which is a disc image. It's already set up to be bootable, just burn it as-is.

---

### Post by wylien on 2006-07-07
great!
for some reason it is defaulting to winrar, but the download is not complete yet, so i'll wait and see what happens.
so, i am reading the tutorial and i just d/l md5summer to verify the file as soon as it is done and then i will get ready to burn this baby with deepBurner :)  wish me luck! haha

---

### Post by wylien on 2006-07-07
cool - cd is finished - it's so easy, i get i better losen up
thanks for all of your help

---

### Post by richbarna on 2006-07-07
> **wylien said:**
> great!
for some reason it is defaulting to winrar, but the download is not complete yet, so i'll wait and see what happens.
so, i am reading the tutorial and i just d/l md5summer to verify the file as soon as it is done and then i will get ready to burn this baby with deepBurner :)  wish me luck! haha

That's because when you installed winrar, during installation you didn't uncheck the association box for "iso".
No big problem, just right click on the iso, choose properties and "open with" and select your burning program.
That way, you can double-click the iso and it will automatically be placed as a disk image in your burning program. 

The only thing you have to do is change the Burn Speed to 4X or 8X. Then press burn.

Good Luck !

---

### Post by wylien on 2006-07-07
i gues i can worry about the partitions once i have formatted the hd and installed windows xp again, correct?

---

### Post by richbarna on 2006-07-07
> **wylien said:**
> i gues i can worry about the partitions once i have formatted the hd and installed windows xp again, correct?

Correct, something like reacocard said :-
windows (for windows, obviously) - ntfs - 20 GB
/ (root filesystem, main ubuntu stuff goes here) - ext3 - 20 GB
swap (linux's virtual memory) - linux-swap - 1 to 2 times your RAM
shared (for sharing files between XP and ubuntu) - fat32 - 60 GB

I would use gparted to split the hard drive in two, create the windows partition first. Then install it to the **second** partition. Once that was done I would again use gparted to creat 3 partitions in the **first** partartition.
The reason being that in the future if anything happens with grub, you can use your live cd to boot up the distro in the first partition.

There are many ways to do this, everybody has there preference, I go for clean and simple myself with only 4 partitions lined up like this :-
[http://ubuntuforums.org/attachment.php?attachmentid=12210&d=1152012736](http://ubuntuforums.org/attachment.php?attachmentid=12210&d=1152012736)

Other people go for more complicated setups, look at catlett's hard drive, it's quite impressive ;) :-
[http://www.ubuntuforums.org/attachment.php?attachmentid=12233&d=1152057440](http://www.ubuntuforums.org/attachment.php?attachmentid=12233&d=1152057440)

---

### Post by wylien on 2006-07-09
so i have 3 hard drives. 

hd#1 -  40gb
hd#2 - 100gb
hd#3 - 200gb

i can only plug 2 hd's - so i was thinking about using hd#2 and patition it this way:

hd#2
20gb - ntfs -> for windows
20gb - ext3 -> / (root filesystem, main ubuntu stuff goes here)
1gb  - swap (linux's virtual memory) - linux-swap - 1 to 2 times your RAM (i have 512mb)
59gb - fat32 shared (for sharing files between XP and ubuntu) 

hd#3
200gb - fat32 shared

does that sound like a good idea?

---

### Post by richbarna on 2006-07-09
Yes, it looks good, 2 things to remember.

1.  Windows Xp will automatically install the MBR to Hd#1,first partition (boot)
2. Remember to overwrite it with Grub when you install Ubuntu after.

Then look at my "sig" later, where it says Grub & Menu.list, It will tell you how to add Windows to the menu.list so that you see it at boot.
|
|
v

---

### Post by Sonofmoog on 2006-07-09
> **wylien said:**
> so i have 3 hard drives. 

hd#2
59gb - fat32 shared (for sharing files between XP and ubuntu) 

hd#3
200gb - fat32 shared

does that sound like a good idea?

Windows can read/write ext3 partitions with a little help.  Google for this file Ext2IFS_1_10b.exe, and install it to give Windows access to your Linux filesystem.  

With this driver installed, you might want to consider making those shared filesystems ext3.  It is more stable and makes better use of the space than FAT32

---

### Post by wylien on 2006-07-10
thanks sonofmoog, i will google it.
i probably wont be able to get to work on it til later this week, but thanks in advance to everyone oin the forums. every one has been great help!
cheers

---

