---
title: "Installation tips"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2006-07-25
I'm going to attempt to install Ubuntu one more time.  This will make the 5th attempt.  I'm trying to set it up for a dual boot with Windows XP.  Every time I do it, Ubuntu does great, but I can't boot Windows anymore.  When I chose it from the menu system I get a blue screen with a lot junk on it and have to reinstall Windows.  The only suggestion I've had that I haven't tried yet is editting the boot order to where I can have Windows appear in the list first.  I'm not really certain how well that will work.  Here are my specs:

Intel Pent 4
160 Western Digital Hard Drive
512 RAM
Sound (although I don't know what kind of card it is, I know it works with Ubuntu)
52x Memorex CDRW
Lucent Winmodem (which is the only reason I'm keeping XP around)

I have both the livecd/alternate cds for Dapper and have tried both.  Anyway...any last minute suggestions would be appreciated before I try this again.

~*~Ash~*~

---

### Post by Dr. Nick on 2006-07-25
Whats your partitions like? Is Xp on the first partition? Ive heard that having xp on any partition but the first can cause problems. Also if it happens again note the blue screen error on windows, may help determine what goes wrong.

I have never had a dual boot issue like that

---

### Post by magnoliablossom on 2006-07-25
WinXP is on the first partition, however for some reason when XP sets up, it leaves less than 1 gig of unused(unpartitioned) space, then creates it's own partition.  I had a suggestion to create my Win partition first but it doesn't work.  XP is arrogant and doesn't recognise any partitions it doesn't make.  You know what is really odd about this entire thing was that I was perfectly happy with XP until I found out about Ubuntu and tried to set it up.  Now I despise Microsoft. lol

---

### Post by Dr. Nick on 2006-07-25
Not sure if youve tried this before or not. 

If you are not opposed to a full dormat and erasing your entire disk then i would do this

Drop in your xp cd, when you get to the stage in xp to partiion your disk erase every partition so all it shows is free space. then make 1 partition and set its size, dont let it take the full drive. format it ntfs/fat32 and dont touch anythig else
Make sure the rest says "free space" or unpartitioned space.

Set up xp on the one partition you made and get it installed, once it works fine then go install ubuntu, either manually partition the free space or tell it to install on auto allocted fre space. I try to avoid any partition resizing when I install OS's, it just takes a little planning ahead in the partition scheme

---

### Post by magnoliablossom on 2006-07-25
I'm not opposed to doing a full format...I've had to do it every time I've gotten the blue screen anyway to get Windows back.  The only thing about that though is that XP is a hog and it's not giving me an option to tell it how  much space to let it have.  Even when I go to reinstall it, it tells me that there are no partitions there (it's not seeing the partitions that have Ubuntu on it).  It's greedy and just assumes it can have it all.

> **Dr. Nick said:**
> Not sure if youve tried this before or not. 

If you are not opposed to a full dormat and erasing your entire disk then i would do this

Drop in your xp cd, when you get to the stage in xp to partiion your disk erase every partition so all it shows is free space. then make 1 partition and set its size, dont let it take the full drive. format it ntfs/fat32 and dont touch anythig else
Make sure the rest says "free space" or unpartitioned space.

Set up xp on the one partition you made and get it installed, once it works fine then go install ubuntu, either manually partition the free space or tell it to install on auto allocted fre space. I try to avoid any partition resizing when I install OS's, it just takes a little planning ahead in the partition scheme

---

### Post by Herman on 2006-07-25
I think some tests are called for here, When you go to the doctor or a mechanic they do some tests before they give you a diagnosis. Computers are no different. I would think that maybe we would find out some useful information about your hard disk if you boot the Live CD and open a terminal and type 'sudo fdisk -l' and also 'sudo fdisk -lu'.
```
sudo fdisk -l
``` ```
sudo fdisk -lu
``` If you can, post the output of at least one of those tests here. 

Normally, the first track (63 sectors) should begin with your MBR and your first partition should begin right after that.  All your other partitions should begin and end on the cylinder boundaries.

In my computer at least, as long as my Windows remains named as partition number 1, it does not actually matter where it is located on the disk.  I have moved my Windows to the other end of my disk, but it still boots perfectly, but it it was allowed to get a different partition number I wouldn't expect it to boot at all.
And the start of the partition is alligned with a cylider boundary. Moving the partition with good disk partitioning software like GParted should be able to automatically fix that problem for you (I hope). Always back up data before using any disk partitioning sofware. (Of course).

I have to go to work soon though, so I will not be here for a few hours, someone else may want to take over if anyone can see the problem.

---

### Post by wpshooter on 2006-07-25
Here's how I would do it.

1) Assuming that you don't have any data on the drive from either O/S that you need to save/backup, I would use a good hard drive wiping utility to get everything off of the drive.

2) Install XP first, look at the partitioning (if any) and delete any existing partitions, then make a partition for XP only and leave the rest of the space unpartitioned.

3) After XP is completely installed and configured, the use the Ubuntu DESKTOP CD and make these partitions: "**/**" (i.e. root) primary/ext3, "**/home**" primary/ext3, "**swap**" primary/swap.

After Ubuntu finishes installing, reboot and see if you can get into each O/S.

Good luck.

---

### Post by Dr. Nick on 2006-07-25
weird, where did you get your XP disk? Is it a full reatil copy or a oem copy you got with a new computer. I have always had the option in the XP install to specify a partition size, I always make atleast 2 partitions on any computer I install XP on, either for backup or to install a Linux aswell. this is off my retail copy, a oem copy may have automated this part of the install causing your problems

---

### Post by magnoliablossom on 2006-07-25
Umm I installed this on a brand new out of the box hard drive.  Which is why I don't mind starting fresh.  All my important things I still have on the old drive.  But it's only a 40 gig hard drive and it's about full, which is why I got a new drive for it.  All these reformats do concern me though.  Could it possibly harm my new drive?

---

### Post by magnoliablossom on 2006-07-25
You are correct...It's OEM and everything it pretty much automated.

> **Dr. Nick said:**
> weird, where did you get your XP disk? Is it a full reatil copy or a oem copy you got with a new computer. I have always had the option in the XP install to specify a partition size, I always make atleast 2 partitions on any computer I install XP on, either for backup or to install a Linux aswell. this is off my retail copy, a oem copy may have automated this part of the install causing your problems

---

### Post by deadgobby on 2006-07-25
There is a on line vid to show how Dual booting with XP/Ubie
video.google.com/videoplay?docid=-6104490811311898236

---

### Post by Aurdal on 2006-07-25
have you tried selecting the free space and hitting "c" for creating a partition? You should get a screen where you can type in the size in MB. I used to have XP on a 10 GB disk that's 10240 MB. For any files or large installations I haf a larger partition.

Hope this will help you.

---

### Post by Dr. Nick on 2006-07-25
ouch the oem is going to get you thier, with a retail copy you have the option to set it all up manually, Is it xp pro by any chance? Thier is a program in XP pro to mess with partition sizes, not sure if it works on the partition windows is installed on or not

EDIT

To answer your format question, I doubt it will hurt the drive really, mine has been formated no less than 30-40 times in the several years Ive had it.

---

### Post by Dr. Nick on 2006-07-25
> **Aurdal said:**
> have you tried selecting the free space and hitting "c" for creating a partition? You should get a screen where you can type in the size in MB. I used to have XP on a 10 GB disk that's 10240 MB. For any files or large installations I haf a larger partition.

Hope this will help you.


Thats what I was thinking, that will usually only work if you have a retail XP copy, most oem copies like he has automate this entire process, most of the time it is set just to erase the whole hard drive and make a single partition out of the entire disk

---

### Post by magnoliablossom on 2006-07-25
It's XP Pro.  I will try to find the option about changing the drive size.  Right now though it's just XP Pro, no service packs or updates or anything (i'm being brave swimming in a world of sharks with no protection lol).  I'm on dail up so updates would take DAYS.  So I'm not bothering with that until I get it working.

---

### Post by Dr. Nick on 2006-07-25
Ok, Look around the control panel under adminstrative tasks( or tools) if forget. I think it is called something like "disk management"

EDIT

try here for specifics on how to get thier
[http://www.theeldergeek.com/disk_management.htm](http://www.theeldergeek.com/disk_management.htm)

---

### Post by magnoliablossom on 2006-07-25
Okay, I'm an idiot...In the Recovery Console of  my XP restore cds, under Advanced Options allows me to configure the partitions.  So, right now, I have Windows using about 65 gig of my hard drive with the rest unpartitioned.  Haven't installed Ubuntu yet.  We'll see what happens. (good luck me)

---

