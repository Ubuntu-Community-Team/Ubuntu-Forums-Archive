---
title: "Install Ubuntu over XP - Can I do so without loosing my Windows Partitions?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by ZootNerper on 2007-08-13
Hi Again,

I'm about to move my last box over to Ubuntu. The first two I just did a fresh install of Ubuntu as they had little on the discs of importance. But this last one has two hard drives with Windows (XP) partitions (NTFS). The main disc has 4 partitions and the second 2. I don't want to loose data on these partitions except the C: drive where there is only XP.

I want to install Ubuntu over the XP on drive C:, but not upset the other partitions. (I don't want a dual boot system) Will Ubuntu be able to read write to these partitions after install?

I've run the Live CD and checked that I can see the drives and their data. But the files appear to be read only. Is this because the files systems are different or the Live CD.

If the file systems are different, Can I change the system without having to loose data? And if so how?

Cheers,

-- Zoot

---

### Post by Lucifiel on 2007-08-13
Okay, you don't want to install anything on the first 2 partitions, right? So, you should type this in Terminal on the Livecd:
> 
sudo fdisk -l 

This command will show you all the partitions you have and their assigned names. Unlike Windows, the partition names in Linux remain constant unless you make any hardware changes like installing a new motherboard. So, you should take note of the names of the first 2 partitions and ensure not to install on them.

If you want to install over WinXP, it's faster to actually get GParted or SystemRescueCd. And then use the Partition manager to delete the WinXP partition. That way, you'll only be installing over empty space.

---

### Post by 5-HT on 2007-08-13
Yup, you can install Ubuntu only to that c: parition, but it is HIGHLY recommended to at least have a separate swap parition. 
[quote=ZootNerper]Will Ubuntu be able to read write to these partitions after install?[/quote] Read access is possible by default. For write access, take a look at ntfs-3g. NOTE: microsoft have never released the specs for NTFS so please use at your own risk. 
[quote=ZootNerper[/quote] Is this because the files systems are different or the Live CD[/quote] Nope, your partition filesystems are untouched with the live CD. To get read-write for NTFS you'll need to install a separate app (like NTFS-3G).

Just installl Ubuntu only to the one parition you want, but you *should* (but do not have to) split that partition in two to make 1) a Ubuntu root partition and 2) a swap parition.

ASIDE: It's a really good idea to create a separate /home partition to keep all your data separate from the system partition--makes reinstalls much, much less painful. 

Cheers,

---

### Post by ZootNerper on 2007-08-13
Hi Lucifiel,

Thanks for your reply. I actually want ti install on the first partition (the Windows C: drive) but leave the other partitions untouched.

However, after I have installed Ubuntu, will I be able to write to these untouched partitions or not? Are the Windows and Ubuntu file systems interchangable? The Live CD showed me I can read my files, but I could not write.

(I'd hate to have to backup all my data and then re-install it all again!)

-- Zoot

---

### Post by Hopeless on 2007-08-13
well do a defrag twice in windows ...download gparted live cd then shrink the NTFS part and a way you go install Ubuntu on the blank part of your c: drive...

Windows is NTFS
Linux is EXT3

---

### Post by anewguy on 2007-08-13
If you boot from the LiveCD, go into a terminal to get the command prompt and type:

gparted     and press enter.  The will start up the GUI partition manager.  You'll be able to see your Windows partitions and any other.  Pick the partition you want to delete, right click on it and select delete.   Next, you can either manually create the Linux partitions (I say partitions, because the swap partition should be considered mandatory, even if technically it's not) in this freed space, or you can just start the installation process.  When the installation process gets to the disk partitioner, don't tell it to use the entire disk, instead select manual partitioning and continue.  You will get a screen where you can select the free space, allocate a small swap partition, and allocate your large ext3 Linux partition.  Everything else on the disk will remain ok.  It will ask about formating and mounting - you'll want it to only partition the new LInux partitions (I think that's the default when you choose manual configuration) but make sure all of the partitions are selected to be mounted.

I would offer one "small" suggestion - if you really want to be able to read/write your Windows partitions, consider making them FAT32 instead of NTFS.  Linux will be able to read/write the FAT32 partitions.  I know this would mean some juggling on your part to get them all converted, but you wouldn't have to take any chances with the NTFS read/write package. 

I hope we have all been of some help.  Please post back with ANY questions and we will all do our best to help you convert your last system to Ubuntu!:)

---

### Post by Lucifiel on 2007-08-13
> **anewguy said:**
> If you boot from the LiveCD, go into a terminal to get the command prompt and type:

gparted     and press enter.  The will start up the GUI partition manager.  You'll be able to see your Windows partitions and any other.  Pick the partition you want to delete, right click on it and select delete.   Next, you can either manually create the Linux partitions (I say partitions, because the swap partition should be considered mandatory, even if technically it's not) in this freed space, or you can just start the installation process.  When the installation process gets to the disk partitioner, don't tell it to use the entire disk, instead select manual partitioning and continue.  You will get a screen where you can select the free space, allocate a small swap partition, and allocate your large ext3 Linux partition.  Everything else on the disk will remain ok.  It will ask about formating and mounting - you'll want it to only partition the new LInux partitions (I think that's the default when you choose manual configuration) but make sure all of the partitions are selected to be mounted.

I would offer one "small" suggestion - if you really want to be able to read/write your Windows partitions, consider making them FAT32 instead of NTFS.  Linux will be able to read/write the FAT32 partitions.  I know this would mean some juggling on your part to get them all converted, but you wouldn't have to take any chances with the NTFS read/write package. 

I hope we have all been of some help.  Please post back with ANY questions and we will all do our best to help you convert your last system to Ubuntu!:)

Well, the reason why I recommmended using another type of cd like SystemRescueCd or GParted is 'cos more than twice, I've encountered issues where I'd deleted a partition in Gparted on the Ubuntu Livecd. But upon rebooting the pc, I found out the partitions were still there. 

And uhh... ntfs-3g is used by millions of computer users: from your home user to your savvy IT corporate user. :P If it was indeed troublesome, there'd have been plenty of protests already. ;) 

And yes, you're darn right about the swap partition. I forgot about that.  xD

---

### Post by Lucifiel on 2007-08-13
> **ZootNerper said:**
> Hi Lucifiel,

Thanks for your reply. I actually want ti install on the first partition (the Windows C: drive) but leave the other partitions untouched.

However, after I have installed Ubuntu, will I be able to write to these untouched partitions or not? Are the Windows and Ubuntu file systems interchangable? The Live CD showed me I can read my files, but I could not write.

(I'd hate to have to backup all my data and then re-install it all again!)

-- Zoot
Oh don't worry. You can use ntfs-3g to read your ntfs partitions. No data loss, no screwy problems at all. :) 

Ahh... then the "first partition" should show up first in the "fdisk" list. I'd want to check the partition though to make sure it's the one you're going to install Linux to. :) 

So, try this:

Step One: Open up Terminal ("Application"---> "Accessories"---->"Terminal")
Type this in Terminal: 
> sudo fdisk -l
(Lists all your partitions)

Step Two: In Terminal, type this.
> sudo umount /dev/partition_name
Where the partition_name is usually something like this: /dev/hdc1 or /dev/sda1
Normally, the partition is already mounted but 'cos the name is kinda confusing, it's better to unmount it and mount it to a different media label. 'Cos in my experience, sometimes the labels change and it's better to keep track of the device name, that is: /dev/sda1 or /dev/hdc1 

Step Three: In Terminal, type this:
> mkdir /media/chicken(or some other name like "abc", etc.)

Step Four: In Terminal:
> sudo mount /dev/partition_name /media/chicken

---

### Post by ZootNerper on 2007-08-13
Thanks Lucifiel and anewguy,

The deed is done, although it didn't quite work as you suggested.

First off, I couldn't boot XP. It's very hot here and my older disc has suffered more than the newer. My computer used to sit upstairs, which gets very hot - up to 40C. Eventually I realized I would be better off downstairs and I am. Only gets up to 32C here - but no mosquito screens (there are upstairs). My older disc is my system disc. Anyway, for some reason it hiccupped today - but only the Windows partition went west.

So, Ubuntu it was. I tried the "chicken" thing but I couldn't make the directory. So, I used started the install. It took me a while to get the disc partitions to work (total ignorance) My old XP partition of 17.5GB was split into 3 - 4GB for root, 1GB for swap, and the rest as /home, though not sure about this choice amongst many!

At one point I couldn't see my old NFTS partitions, but they came back.

So, now I have Ubuntu running everything I need - my old HP wireless keyboard (best keyboard I've ever had), World Community Grid's Boinc and the BBC World Service. Of course, it plays my mp3s, opens old MS Word docs etc. too.

I will try nfts-3g (is that the name) another day - it's late here.

Thanks for all the help and the offer of more. The encouragement contained was very useful.

-- Zoot

---

### Post by ZootNerper on 2007-08-18
Hi Folks,

Just an update.

Under Ubuntu i ran NTFS-3G and it didn't like the fact that because Windows had crashed before I installed Ubuntu it had left the discs in an erronious state. Can't remember the exact error. Anyway, it removed all the disc icons from my desktop and that was that. 

My solution was to re-install Windows, run chkdsk on every partition (no idea if this was necessary). Then to shift everything off one disc and then re-install Ubuntu and partition/format this free disc Linux style as part of the installation. Then shift everything off another disc and format the newly freed drive.

Took a while, but I figure I am not going back. I would have eventually done it anyway, it just got forced on me. Never could understand converstions - you work in one system or the other, not both (I was a teenager when Britain went from Imperial measures to Metric)

That's all.

-- Zoot

---

