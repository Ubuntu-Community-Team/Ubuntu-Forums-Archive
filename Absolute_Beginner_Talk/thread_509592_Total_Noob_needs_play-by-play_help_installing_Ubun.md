---
title: "Total Noob needs play-by-play help installing Ubuntu..."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Penguinista661 on 2007-07-25
I've had it with Windows. I can't take it anymore! :mad: Would someone out there in UbuntuLand help me install 7.04?
Yeah, I've read the threads explaining this stuff but I'm such a TOTAL NOOB I don't know what all those strange Linux words mean. :confused:
Problem is, since I'm a TOTAL NOOB. I've tried installing FeistyFawn on my harddrive thats already partitioned. One side has Windows on it, the other is blank. Thats the side I wanted Ubuntu on, but it's asking me questions I don't understand & I don't want to do anything because I DON'T KNOW what I'm doing! I was wondering if I could get some live help from someone willing to talk me through the installation....yeah, like "Tech Support". Thats how much of a noob I am! I'll pay for the call!! It would be GREATLY appreciated....
This feels just like asking for directions while driving.....how embarrassing!!
 
P.S. Once I get comfortable operating Ubuntu, transfering files, getting online, etc. Windows is going out the Window!!

---

### Post by FELIX CANINO on 2007-07-25
First Off Ask Ur Question Again In All Caps Locks Then Mayb Just Mayb Ull Be Cool Enough To Deserve An Answer From Me God I Cant Believe I Might Be Helping A Noob

---

### Post by overdrank on 2007-07-25
> **Penguinista661 said:**
> I've had it with Windows. I can't take it anymore! :mad: Would someone out there in UbuntuLand help me install 7.04?
Yeah, I've read the threads explaining this stuff but I'm such a TOTAL NOOB I don't know what all those strange Linux words mean. :confused:
Problem is, since I'm a TOTAL NOOB. I've tried installing FeistyFawn on my harddrive thats already partitioned. One side has Windows on it, the other is blank. Thats the side I wanted Ubuntu on, but it's asking me questions I don't understand & I don't want to do anything because I DON'T KNOW what I'm doing! I was wondering if I could get some live help from someone willing to talk me through the installation....yeah, like "Tech Support". Thats how much of a noob I am! I'll pay for the call!! It would be GREATLY appreciated....
This feels just like asking for directions while driving.....how embarrassing!!
 
P.S. Once I get comfortable operating Ubuntu, transfering files, getting online, etc. Windows is going out the Window!!

Hi and welcome maybe this will help.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
And also this sticky has some good info
[http://ubuntuforums.org/showthread.php?t=232059:popcorn:](http://ubuntuforums.org/showthread.php?t=232059:popcorn:)

---

### Post by Penguinista661 on 2007-07-25
Thanks for the links Overdrank.
I got as far as clicking "manually edit partition table".  The next screen shows the different partitions on the harddrive but I don't want to foul anything up so I don't know what to do after that. :confused: ](*,)

---

### Post by regomodo on 2007-07-25
backup all your documents/files before we get flamebait. Also, backup to a totally separate drive, not partition

---

### Post by Penguinista661 on 2007-07-25
All my stuff is backed up on an external harddrive

---

### Post by overdrank on 2007-07-25
> **Penguinista661 said:**
> Thanks for the links Overdrank.
I got as far as clicking "manually edit partition table".  The next screen shows the different partitions on the harddrive but I don't want to foul anything up so I don't know what to do after that. :confused: ](*,)

Ok you chose manual partition, so how many partitions are on the drive?

---

### Post by Penguinista661 on 2007-07-25
Just 2 partitions. 1 for Windows XP, 1 empty for Ubuntu.

---

### Post by overdrank on 2007-07-25
> **Penguinista661 said:**
> Just 2 partitions. 1 for Windows XP, 1 empty for Ubuntu.

Then you are set to select the one for ubuntu and continue following the links provided. And you will have to create a swap partition fo about twice the amount of memory you have. Good luck!:popcorn:

---

### Post by Penguinista661 on 2007-07-25
Thanks for the help!!

---

### Post by Penguinista661 on 2007-07-25
I've just come upon something else in the installation process that I don't know what to do....
In the Edit Partition section:
_New Partition Size_: 250048 MB - Do I leave that as is or do I change it? If so, what do I change it to?
_Use as_: ????
There are all kinds of different options to put in such as NTFS, FAT 16 & 32, EXT 3 & 2, swap, reiserfs, JFS, XFS...
I want to transfer files from my Windows partition to my Ubuntu partition, so should I use NTFS since thats what Windows uses??

---

### Post by overdrank on 2007-07-25
> **Penguinista661 said:**
> I've just come upon something else in the installation process that I don't know what to do....
In the Edit Partition section:
_New Partition Size_: 250048 MB - Do I leave that as is or do I change it? If so, what do I change it to?
_Use as_: ????
There are all kinds of different options to put in such as NTFS, FAT 16 & 32, EXT 3 & 2, swap, reiserfs, JFS, XFS...
I want to transfer files from my Windows partition to my Ubuntu partition, so should I use NTFS since thats what Windows uses??

If that is the new partition for ubuntu then use EXT 3 , and select the mount point as root with this symbol only  /
:)

---

### Post by doomster on 2007-07-25
ok assumiing that 250048 is all the space you qwanna spend on ubundu (25GB) , make 1 partition 24000mb Formated as "ext3" and with mount point "/" , and 1 partition of 1000mb~ formated as swap.
this should be enought to get you through the rest of the install progress

---

### Post by doomster on 2007-07-25
> **FELIX CANINO said:**
> First Off Ask Ur Question Again In All Caps Locks Then Mayb Just Mayb Ull Be Cool Enough To Deserve An Answer From Me God I Cant Believe I Might Be Helping A Noob

felix if you wanna have fun, be more than welcome to visit  	Ubuntu Forums > The Ubuntu Forum Community  > Forum Community Discussions>Community Cafe.

here we help ppl around their first steps in ubuntu world :D

---

### Post by Penguinista661 on 2007-07-25
I tried selecting the mount point as root with the / symbol but it didn't give me that option.  It only gave me /dos & /windows.  What now??
Thanks for the tips Doomster but I don't know how to partition a harddrive in Ubuntu.  How would I do that?

---

### Post by doomster on 2007-07-25
just select the 24000 and format ext3 and hit ok
then reselect the current partition, and hit edit
now it should have an option as "/" . if not  just force it by typing it your self (not selecting any other. select the space and type /  )

---

### Post by Penguinista661 on 2007-07-25
I tried partitioning the drive to 240000mb but a note popped up and said "too large size".  The original size of the partition is 250048mb.  What now?

---

### Post by doomster on 2007-07-25
ok . lets reroll. how much space do you have to spare for ubuntu?

---

### Post by Penguinista661 on 2007-07-25
The partition size is 250048mb.

---

### Post by doomster on 2007-07-25
first of all you will work on unpartitioned space.. delete the partition that was ment to be for linux if there is one.
then create the following partitions as mentioned before.
1 248500Mb partition formated as ext3, and mount point "/"
1 1000mb partition formated as swap.

these are the 2 partitions needed for linux to work.
with such space available i would prefer to make this build
1 20000Mb partition formated as ext3 and mount point "/" for your system files
1 1000mb partition formated as swap and
1 partition with the rest space (about 229000MB) formated as ext3 partition and mount point "/home"

this way whatever happens later on at /home folder( where you mostly have access as a user in linux) doesnt affect your base system

---

### Post by Penguinista661 on 2007-07-25
Thanks for all your help Doomster. I'm going to try to set it up the way you would do it, but I gotta go pick up groceries for dinner first....
I'll post later & let you know the outcome.

---

### Post by Frak on 2007-07-25
Can you post every word, phrase, or paragraph you don't understand, and I could translate them to English as much as I can. :)

---

### Post by Penguinista661 on 2007-07-25
Ok...I deleted the prior partition and was going to create the partitions you recommended but there are some choices it asks me to select and I don't know which one I should pick.
Type for the new partition: Primary or logical?
Location for the new partition: Beginning or end?
Whatever choices you recommend, thats what I'll do but should I do them all the same for all 3 partitions?

---

### Post by Frak on 2007-07-25
Wait, you didn't use the guided partitioning?

---

### Post by Penguinista661 on 2007-07-25
No, I didn't use the guided partitioning because I was afraid it would wipe out the partition that Windows is on...I've never used the guided partitioning before.

---

### Post by Frak on 2007-07-25
Its pretty stable.
How big is your drive, how much do you want to be used by Ubuntu, and how much is Windows using right now?

---

### Post by Penguinista661 on 2007-07-25
Windows is using something like 161000MB right now. I originally had equally partitioned the harddrive into two sides of 250048MB each, planning one side for XP and the other for Ubuntu but just deleted the unused partition and was going to go with Doomster's recommendation when I came upon the options it asked me for & I don't know which choice to pick.

---

### Post by Frak on 2007-07-25
When it comes to the Guided Partitioning screen, move the slider to 50%, then click next.

---

### Post by Penguinista661 on 2007-07-25
It's not going to wipe out the whole harddrive is it?  I'm guessing it's going to partition the empty part of the harddrive & leave the part of the harddrive with XP alone
I still want to keep the partition with XP on the harddrive for now.

---

### Post by Frak on 2007-07-25
Unless there's something wrong with your hard drive.
It will only take what you tell it to take, it will only use what it needs.

---

### Post by Penguinista661 on 2007-07-26
Thanks Frak, I'll try it tomorrow.  Time to hit the sack...

---

### Post by Penguinista661 on 2007-07-26
I've thought about it and I'd rather use Doomster's method of partitioning the harddrive, no offense to you Frak :)
Plus, it'd teach me a little more about Ubuntu if I do it somewhat manually.  Now I'm just wondering what buttons to push...
Type for the new partition:  Primary or logical?
Location for the new partition: Beginning or end?
Should the answers I give be the same for all 3 partitions I'm going to create?
Thanks in advance for the help!

---

### Post by Frak on 2007-07-26
Primary
End
the last partition should be Logical and Swap type
EDIT
But you'll have to tell Ubuntu where you put the Swap Partition.

---

