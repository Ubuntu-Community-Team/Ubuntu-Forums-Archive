---
title: "Setting up Dual Boot Ubuntu with XP."
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by bobrath on 2006-07-03
I could do with a little help with that partioning. I have 4 partitions on my XP system. C: , D: , E: , F:.
C: - root
D: - files
E:-files
F: - files.
 How should I partition my system when I install Ubuntu , so that all files is C: and D: are intact ?
Could use some help on Ubuntu partition. 
COmplete NOOB

---

### Post by bobrath on 2006-07-03
I forgot to say that I had ONE Hard disk of 40 GB Capacity.

---

### Post by Jagot on 2006-07-03
Have a look at this guide:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

You're going to need to resize one of those partitions to fit Ubuntu on there so just go for the one with the most free space.

---

### Post by dderolph on 2006-07-03
Well, he may not need to resize. It depends on the current size of his partitions, right?

---

### Post by Jagot on 2006-07-03
Well if he doesn't have any free unpartitioned space then he's going to need to.

---

### Post by bobrath on 2006-07-03
I'll need a little more details people....
HELP

---

### Post by Jagot on 2006-07-03
Have you read the guide that I posted?  It tells you most things that you need to know.  Firstly, do you have any unpartitioned free space on your hard disk, or are the partitions taking up all of the 40gb?

---

### Post by Frank Golden on 2006-07-03
Hi All, 
   I agree with Jagot read the tutorial, However make sure you use the
alternative install CD not the Desktop CD. You have much more flexibility in 
your choices. Plus the tutorial is really written for the Alternative CD. Just make sure
you back up your XP install and first read sections about removing Ubuntu and reinstalling your Windows MBR in case something goes wrong. I used this method
to setup a XP dual boot. If you have room make a FAT32 partition to share files
between the two OS's. Really the above mentioned tutorial explains this all better than I can. I have this tutorial as well as many others bookmarked in a folder
titled Linux stuff. I am a relative noobie with Linux/Ubuntu. But I have learned a lot
in a short period of time and with the help of these forums I will learn a lot more. 
One thing I learned early was to defer to people more experienced than myself. LOL 
   Be patient and you will be rewarded with a dual boot machine where you can
move flawlessly between XP and Ubuntu. You might even find someday you don't
seem to be booting XP as often as you used to. Not entirely a bad thing. :D

---

### Post by catlett on 2006-07-03
For you to install ubuntu you will have to do some advanced stuff. I would recommend buying a used 10gb  hard drive off of ebay. They are cheap and will make your life easy. All you would do is install it as the slave and choose that drive during installation. Because you are selecting an entire drive you can then have the installer automatically create the partitions needed and install ubuntu. Otherwise this is what you will have to do. 

Your problem is a hard drive can only have 4 primary partitions and you already have 4.
You can have many logical partitions though. The problem is 1 primary partition has to become an extended partition. Then you create logical partitions inside of the extended partition.
So for you to install ubuntu  (this is assumes you have free space on 1 of your partitions to handle the install) you would need to select the partition that had the free space for ubuntu. Back up that data somewhere. Use a partitioning program to delete that partition. Create an extended partition out of the now deleted space. Create 3 logical partitions. 1 formatted to "ntfs" for your files you have backed up. This needs to be large enough to hold the files.
Now you need 2 more partition for ubuntu. Create one that is twice your ram in size for the swap partition i.e. 256mb ram = 512mb swap. Format that partition to "linux-swap". The 2nd partition should be around 8gb or more depending on the space you have for the root partition. Format that as "ext3".
Finally when you run the installer you cannot choose "automatically" partition your drive,  you need to choose "manually edit the partition table". This way you can choose the 2 partitions you created as the place for ubuntu. That's it. 

That is why I recommend getting a 2nd hard drive and installing ubuntu on that.:D

---

### Post by dderolph on 2006-07-03
"Your problem is a hard drive can only have 4 primary partitions and you already have 4."  He has 4 partitions, but we don't know that he has 4 primary partitions.  Right?  You seem to be assuming those partitions are all primary partitions.  But, that may not be the case.

---

### Post by catlett on 2006-07-03
I doubt they are logical partitions. The default when you partition with MS is to make primary partitions. It would take a few steps to make logical partitions but it is possible.
Either way he still has to back up data and create new partitions.

For the sake of full disclosure lets assume you have 2 primaries and 2 logical partitions. The issue is you need to clear space for ubuntu. Right now you have 4 partitions and no unallocated space. Having logical instead of primary partitions only removes one step, it is still advanced.
First choose the partition that has at least 10gb free space. Get a partitioning program. Resize that partition to free up 10 gb. Create a primary partition twice your ram and format it swap. Create a primary partition that uses the rest of the unallocated space and format it ext3. Run the installer and select "manually edit the partition table". Select the 3rd primary partition for swap and select the 4th primary partition for root. (partitions are not labeled C,D,E,F in linux. so the 3rd and 4th primary partitions will be labeled /dev/hda3 and /dev/hda4 be sure to select thge right ones. If you choose the other 2 primaries you will erase windows and all your data)

As you Can see having primary partitions available doesn't make it that much easier. So once again buy a second hard drive. I buy 10-15gb drives at my local computer shop for $20. They install in under 5 minutes. If you don't have a local shop go on eBay. Trust me it will be far easier AND SAFER. You can select "automatically partition" and the installer will do everything foir you. It will partition, format and install the OS.. Plus with a slave drive your main drive isn't touched except for the mbr if you choose to install grub. (even them you can choose to install grub to a floppy and your master won't be touched at all)

---

### Post by dmann on 2006-07-03
Somebody should try to assimilate this guide (with the authors permission) into official ubuntu documentation; if that user's account goes down or a server crash occurs and no backup is available, that information could be lost.

Dan

[QUOTE=Jagot]Have a look at this guide:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

You're going to need to resize one of those partitions to fit Ubuntu on there so just go for the one with the most free space.[/QUOTE]

---

### Post by bobrath on 2006-07-04
[QUOTE=Jagot]Have you read the guide that I posted?  It tells you most things that you need to know.  Firstly, do you have any unpartitioned free space on your hard disk, or are the partitions taking up all of the 40gb?[/QUOTE]
 But I have the Live CD

---

### Post by confused57 on 2006-07-04
[QUOTE=bobrath]But I have the Live CD[/QUOTE]

Boot up with the Live CD, and open a terminal(Applications---Accessories---Terminal), enter:

```
fdisk -l
```
The -l is a small "L".

I believe this will tell us the size of your partitions...I believe you mentioned, you were concerned about keeping the C & D partitions intact(Ubuntu should show them as hda1 & hda2).  Catlett gave you some good advice about partitioning,
you'll probably need to backup your data on the last partition, then if it's large enough(at least 5 GB), you might be able to install Ubuntu onto that partition(root(/) will be a primary partition and swap will be a logical partition by default during the installation.
See the 3rd link in catlett's signature for installing with a live cd.  I hope I've read everything correctly in this thread and these suggestions could help.

If the LiveCD is working on your computer, use it for awhile maybe for a week or 2 getting used to the OS...read, read, and read some more in the forums.
Do you have the Windows XP installation CD(not a recovery CD), just in case your system isn't bootable after installing Ubuntu?  You'd need that to fix your Windows mbr, so you can boot Windows again.
Also, could you tell us a little about your computer specs(processor, ram, internet connection, wireless, etc).  That'll help anyone giving you advice.

---

### Post by SizzleBeast on 2006-07-04
I was able to pull off the 7 partitions on one hd (max possible). If you would be interested in doing it, i may be able to help you out.

---

### Post by krazykirk on 2006-07-04
I think dual booting XP and Ubuntu is pretty easy! I do it, and i have lots and lots of partitions (ntfs) in windows! I used partition magic to resize my partitions so i had 10 gb of unallocated space, then when i was installing ubuntu, I told it to use the unallocated space and GRUB just configured the bootloader by itself.

---

