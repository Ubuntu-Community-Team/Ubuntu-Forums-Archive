---
title: "Ubuntu 8.04 or 7.10 on PPC Help"
date: 2009-03-10
forum: Apple Hardware Users
---

### Post by Unix-Man on 2009-03-10
Hello  

Im making a new partition with disk utility and the new partition is formatted under "Mac OS Extended Journaled" can i boot Gutsy 7.10 or Hardy 8.04 on that partition???

And if i ever get it to install on the partition how do i make the computer boot from the partition? 

Hope this all made sense Lol thanks Unix-Man

Also if possible i would prefer not to Format my hard drive i don't want to go through the trouble.

---

### Post by avtolle on 2009-03-10
You will need to reformat that partition to ext2 or ext3 (I prefer the latter), which should be done by the installer I believe when you choose to install on that partition. I would suggest using the manual partitioning option myself, choosing that partition to be used as ext3, mountpoint of / (root); and don't forget to create a swap partition as well. Good luck.

---

### Post by Unix-Man on 2009-03-10
Well it's creating the partition as i type and it's been saying "Modifying Partition Map" for about an hour how long should this take??? i have an 80 GB hard drive and the partition i made is 10 GB's


Also what is a Swap partition and how do you make one? im kinda new to all this be patient with me LOl 

Just thought i'd say my Mac is a 15' PowerBook G4 1.5Ghz 512MB RAM 80GB HD you know

---

### Post by tiresia on 2009-03-10
Are you planning to install MacOSX as well?
Or is it already installed? 

Back up important datas if this is your first installation!!!

---

### Post by Unix-Man on 2009-03-10
It's already installed i have Leopard 10.5.6 
Umm and im using Disk Utility inside OS X to Partition it

---

### Post by tiresia on 2009-03-10
> **Unix-Man said:**
> It's already installed i have Leopard 10.5.6 
Umm and im using Disk Utility inside OS X to Partition it
You can't make a partition on the same Disk where your System is running.
Or do you have a second partition. Please, be careful, you can damage your System

---

### Post by Unix-Man on 2009-03-10
Honestly im not really sure this is my Disk Utility Window right now

---

### Post by tiresia on 2009-03-10
Ok, as I said, BACK UP YOUR IMPORTANT DATAS!!!

You have downloaded the LiveCD (Desktop) Ubuntu 8.04.1
Burn it with the Disk Utility at low speed.

When you are ready, start from the CD pressing C
Be patient, it can last a couple of minute to start.

Then go in System > Administration > Partition Editor (Gparted)
There you can resize your Disk, leaving 10-15 GB for Ubuntu.
When you are done, install Ubuntu choosing the automatic installation.
Choose to install Ubuntu on the free space (that you created resizing your Disk)

Be aware that if you want to exchange datas between the two System, it is safer to have a third partition (Share). If you want to do so, after having resized the MacOSX Volume, and before installing Ubuntu, create on the free space a Partition fat32.
A possible solution for your HD could be:
MacOSX 60 GB
Ubuntu 10/15 GB
Share 5/10 GB

Of course if you have an external HD, you can use it as Share Partition, and you can just have two partitions for the OS's on the internal HD

---

### Post by Unix-Man on 2009-03-10
Alright makes perfect sense Thanks 

But i already burned the .iso to a disk at high speed will this be an issue?

---

### Post by tiresia on 2009-03-10
> **Unix-Man said:**
> Alright makes perfect sense Thanks 

But i already burned the .iso to a disk at high speed will this be an issue?
Well, try, it is a problem more on very old Optical Drives.
If you have problems with video (black screen), reboot and at the first prompt type:```
live-nosplash-powerpc video=ofonly
```

---

### Post by Unix-Man on 2009-03-10
Okay i got it to boot from the disk, now for some reason inside Gparted it will only let me resize my current OS X partition by 128 (MiB) this is really weird on OS X it says u have 20 GB's free

---

### Post by Unix-Man on 2009-03-10
Okay i got it to boot from the CD, but for some reason inside Gparted when i click resize/move on my OS X partition it will only let me change it by 128(MiB) awkward this is what it says 


Free Space Preceding (MiB):128

New Size (MiB): 76191 

Free Space Following (MiB): 0

---

### Post by tiresia on 2009-03-10
Can't you change the New Size, making it smaller??

---

### Post by Unix-Man on 2009-03-10
Nope the arrows on the side are not illumed there for i cannot click them Lol and i can't change it with text either

---

### Post by Unix-Man on 2009-03-10
Yea nvm it can't be changed

---

### Post by tiresia on 2009-03-10
Try following. Close gparted. Open a terminal (applications > accessories > terminal) and type:```
gksudo gparted
```

---

### Post by Unix-Man on 2009-03-10
Alright all it did was launch G parted and it didn't change anything

---

### Post by tiresia on 2009-03-10
Can you please thak a picture of it (Applications, Accessories, Take Screeshots)

---

### Post by Unix-Man on 2009-03-10
i tried to fit all the windows

---

### Post by pxwpxw on 2009-03-10
> **tiresia said:**
> Can you please thak a picture of it (Applications, Accessories, Take Screeshots)

Seems to be hfs+journalled - it needs disable journalling?

---

### Post by Unix-Man on 2009-03-10
Can you disable Journaling from the Ubuntu CD?

---

### Post by avtolle on 2009-03-10
> **Unix-Man said:**
> Can you disable Journaling from the Ubuntu CD?
AFAIK, the answer to your question is no. Journaling must be disabled from within OSX.

---

### Post by Unix-Man on 2009-03-10
Well journaling is not enabled because in Disk utility there is no option to Disable Journaling only Enable and it's not illumed and i can't click it

---

### Post by pxwpxw on 2009-03-10
> **Unix-Man said:**
> Well journaling is not enabled because in Disk utility there is no option to Disable Journaling only Enable and it's not illumed and i can't click it

OK, you disable it in OSX with a terminal command I will give you, but first need to get back in OSX and check with  Disk Utility again to verify your OSX partition  and see what you have there.

---

### Post by Unix-Man on 2009-03-10
Like open Disk Utility and click on Verify LOL??

---

### Post by pxwpxw on 2009-03-10
> **Unix-Man said:**
> Like open Disk Utility and click on Verify LOL??

Yes, but also need to see your partitions - what happened about the 10GB shown in the pictuire?
You can also see these in terminal using

diskutil list

---

### Post by Unix-Man on 2009-03-10
Here is what i got from that terminal command 

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     Apple_partition_scheme                        *74.5 Gi    disk0
   1:        Apple_partition_map                         31.5 Ki    disk0s1
   2:                  Apple_HFS Nick's HD               74.4 Gi    disk0s3
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *3.8 Gi     disk1
   1:                 DOS_FAT_32 UNTITLED                3.8 Gi     disk1s1





And at the moment im repairing my disk permissions

---

### Post by pxwpxw on 2009-03-11
> **Unix-Man said:**
> Here is what i got from that terminal command 

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     Apple_partition_scheme                        *74.5 Gi    disk0
   1:        Apple_partition_map                         31.5 Ki    disk0s1
   2:                  Apple_HFS Nick's HD               74.4 Gi    disk0s3
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *3.8 Gi     disk1
   1:                 DOS_FAT_32 UNTITLED                3.8 Gi     disk1s1





And at the moment im repairing my disk permissions

What is /dev/disk1 3.8GB ?

---

### Post by Unix-Man on 2009-03-11
Thumb Drive LOl sorry about that i forgot it was plugged in

---

### Post by pxwpxw on 2009-03-11
> **Unix-Man said:**
> Thumb Drive LOl sorry about that i forgot it was plugged in

OK, best remove it till needed.

Here is what should happen -

You may need use the Mac OSX Install DVD Disk Utulity, but try from OSX first.

Make the 10GB partition as shown in your first picture as EMPTY NAME, then just Erase the 10GB   to Mac OS Extended.

Then restart and verify both partitions again in OSX Disk Utility.

Then in the Ubuntu Live CD, gparted, just delete that 10GB partition leaving it unallocated.

Then in the installer partitioner choose to install in the free space and it will make root swap and bootstrap partitions automatically in the 10GB.

---

### Post by Unix-Man on 2009-03-11
> **pxwpxw said:**
> OK, best remove it till needed.

Here is what should happen -

You may need use the Mac OSX Install DVD Disk Utulity, but try from OSX first.

Make the 10GB partition as shown in your first picture as EMPTY NAME, then just Erase the 10GB   to Mac OS Extended.

Then restart and verify both partitions again in OSX Disk Utility.

Then in the Ubuntu Live CD, gparted, just delete that 10GB partition leaving it unallocated.

Then in the installer partitioner choose to install in the free space and it will make root swap and bootstrap partitions automatically in the 10GB.


Well the reason i stopped the 10GB EMPTY NAME Partition was because it just sat there for about 3 hours saying "Modifying Partitions Map" should it take that long?

Also what do you mean by "Erase the 10GB to Mac OS Extended." when i make a new partition it only lets me choose Mac OS Extended Journaled

---

### Post by pxwpxw on 2009-03-11
> **Unix-Man said:**
> Well the reason i stopped the 10GB EMPTY NAME Partition was because it just sat there for about 3 hours saying "Modifying Partitions Map" should it take that long?

No, but I'm hoping it will do better - if you  found repair was needed. 
Do it using the OSX Dvd Disk Utility so your OSX partition is not in use.  
May take 1/2 hour or more if it has to move existing files in OSX to make the space, but not 3 hours.

---

### Post by pxwpxw on 2009-03-11
I forgot, make sure you empty the trash in OSX.

---

### Post by Unix-Man on 2009-03-11
Alright it says Partition Failed because of an error. I think i need a different way to approach this it doesn't want to partition in OS X and the Gparted will not resize my current Partition im not sure what to do

And i don't have an OS X install DVD

---

### Post by pxwpxw on 2009-03-11
> **Unix-Man said:**
> Alright it says Partition Failed because of an error. I think i need a different way to approach this it doesn't want to partition in OS X and the Gparted will not resize my current Partition im not sure what to do

And i don't have an OS X install DVD

OK go the gparted resizing way -

From your list, macosx is disk0s2
Disable journalling in terminal
```

im81:~ pxw$ diskutil disableJournal /dev/disk0s2
Journaling has been disabled for volume mosx on disk0s2

```
Check in Disk Utility it is not journalled.
As a last resort read 
man diskutil

Then try the resizing again in ubuntu gparted, leave 10GB free space for the partitioning as already described.
When ubuntu is finally installed, do the OSX verify/repair again.

---

### Post by tiresia on 2009-03-11
Hi UnixMan, how is it going? Sorry for leaving you, but I had to go to bed yesterday...

---

### Post by Unix-Man on 2009-03-11
Okay, Thanks for all your Help. It finished resizing the partition now when i run the installer Should i click 

"Guided - use the largest continuous free space" or 

"Manual" 

Also would you recommend i install 8.04 or 7.10

---

### Post by tiresia on 2009-03-11
> **Unix-Man said:**
> Okay, Thanks for all your Help. It finished resizing the partition now when i run the installer Should i click 

"Guided - use the largest continuous free space" or 

"Manual" 

Also would you recommend i install 8.04 or 7.10

Guided - free space
8.04

---

### Post by Unix-Man on 2009-03-11
Alright Thanks :) now once it installs how do i make the computer boot Linux? 


Also i can't turn up the Panel Brightness when im booted from the CD will this fix with installing it?

---

