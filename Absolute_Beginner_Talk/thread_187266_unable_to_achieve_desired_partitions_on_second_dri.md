---
title: "unable to achieve desired partitions on second drive"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by keith whitehouse on 2006-06-02
Hi there,

I decided to download the new Dapper Drake, and install it on my second hard drive, an 80 Gig Sata drive The first drive (another Sata drive of 160 Gig) still has Windows on it. I am running Hyperos on the first drive and there are 10 partitions each doing just one thing, like "burning", "TV", "database", "Internet" etc etc. Best not to let Windows get confused.

I already had Dapper Drake Beta installed on drive 2 with a FAT32 area which I use when in Windows for compiling videos.

In PQMAGIC before I started the fresh install I had the following.

Unallocated 7.84 MB
Extended    50.94 GB
Fat32          48.83 GB
Fat32            1.08 GB
Linux Swap   1.03 GB
EXT3            23.58 GB

the EXT3 was for linux root
the FAT32 was for the data file
and then the swap file.

The unallocated 7.84 MB is right at the front of the partitions and I cannot do anything with it, I know that you cannot extend to the right so I finally deleted all of the partitions to the right in the hope that I could make this first unallocated (very small) 7.84 MB area larger ie to 10 GB to hold the root. But whatever I tried I could not make it any larger.

I have played around with the partitioning in the new Dapper Drake without any luck. I tried to manually configure them on numerous occasions but I could not make a primary drive, and I also let the program set it all up automatically, but try as I might I was unable to achieve what I wanted. Out of desperation as I needed to run Windows (to run the large database daily (SB4W)), I had to in the end let the program automatically partition, and what I am left with is 

Linux EXT2   7.8 MB                                Primary      Status      None
Linux EXT2 74.834 MB                            Primary                      Active
Extended 1.774.7 MB                             Primary                      None
Swapspace2 Linux Swap 1.774.7 MB     logical                         None

(I notice that the ridiculously small first area is still there)

What I would like is

/ 10 gig
home 50 gig
swap 2 gig
and the rest as Fat32? for the data from the Windows programs for video editing.

any help or advice would be appreciated, and I hope that you are able to understand what I am talking about.

A further problem in the Dapper Drake Partinioner is that my partitions on my main drive populated the menu and made the bottom options unavailable to me, as they were off the bottom of the screen.

It has been a long trying day and I am off to bed.

best regards keith

---

### Post by CompShrink on 2006-06-02
I would suggest downloading the Ultimate Boot CD, boot off that, and choose INSERT, which is a small Linux distro made for repairing systems. The CD has a lot of useful tools, and it's a good thing to keep around anyway.

[http://pcinfo4u.net/ubcd/ubcd34-full.zip](http://pcinfo4u.net/ubcd/ubcd34-full.zip)
or
[http://y.mrbass.org/ubcd34-full.zip](http://y.mrbass.org/ubcd34-full.zip)

When you boot into INSERT, on the desktop there is an icon for QTParted. You can try using that, it's a nice graphical partition manager.

You sound like you know what you're doing, but the partition managers you tried just aren't cooperating. I've had experiences like that, sometimes just trying a different one works, or at least gives you a useful error message you can search for. If QTParted still doesn't work, please post in this thread what error you get.

---

### Post by catlett on 2006-06-02
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) This is my favorite partitioner. It is a quick download, only 30mb. The best thing about it is it's a live cd so your drive is not mounted and you can do all the partititoning right there. No need to reboot and have PM run a batch file.
Anyways your original issue may have been because everything other than the 7mb was an externded partition. I'm not sure but it might be that you can't have just an extended partititon, you need a primary as well. The  partitioner may have been keeping the first sector of the drive as a primary for boot reasons, I don't know but it doesn't matter now.
Boot to gparted. You can have 4 primary partitions so all the partitions will be primary just to be safe.
Delete all partitions. Choose "new" and create a partition. The nice thing about gparted is it has a graphical interface. You slide a bar graph to make the size of the partition.
 Make your root first. Because this will have your boot partition and you'll have it up front. Make an ext3 primary partition.  Your root is only the base install and anything you add as far as applications, 5gb is enough but if you feel more comfortable you can do 10gb since you have the space.
Next make a swap. The rule of thumb is twice ram i.e. 256mb ram = 512mb swap.
You have 1.3gb already that's fine. Make a 1.3gb partition and format it linux swap.
Last is home. Home is for everything else. If you are the only user then all the space is yours. As you know in linux you only have control of home as a user (you can access anywhere but you have to be root aka sudo in ubuntu) So any documents,mp3s,videos will be downloaded and stored in home. So make a new partition formatted ext3 for home at 69.7gb.
When you get to the dapper live partitioner it will have a page for your partitions. Just choose the mount points from the drop down boxes. The box in front of 69.7gb make "home". The box in front of 1.3gb make "swap" and the box in front of 10gb make " / "(root).
It will lists all your partitions on your first drive. Just choose the default mount points. The only IMPORTANT thing is in the live cd installer it will have circles to check off after the partitions with "format?" written above. Only format the swap,home and / partitions, nothing else.
The only issue left is people are having a hard time with sata drives and the install. Especially with installing grub to the mbr. Good luck and search about sata issues on the forum. (I don't have one so I don't know)

---

### Post by keith whitehouse on 2006-06-03
Hi Compshrink and Catlett,

I will download gparted and have a go with it this afternoon.

Many thanks for your advice and help

best regards keith

---

### Post by keith whitehouse on 2006-06-03
Hi Compshrink and Catlett,

I downloaded the set of Linux tools from post one, and then downloaded gparted livecd from the second post. I then printed out both replies.

In Nautilus as per instructions in Ubuntu FAQ guide page 2 item 1.5 I burned the images one at a time onto seperate CD-RW discs and then tried to reboot from the gparted disc. I could not and I could not boot from the linux tools disc either, not bad none from 2. I restarted Ubuntu and copied the gparted file to disc, and then rebooted into Windows. On my burn partition I used Nero Burning Rom to burn the image to one of the previously unbootable discs. I reformatted it and then burned a new image. This worked first time and I was able to boot from it.

Catlett, your instructions worked faultlessly. I completed the installation of Ubuntu and when I finally arrived at the desktop I was surpised to see all 10 partitions of my first hard drive listed, and I have never seen that before.

Many thanks for the help from both of you, it was very much appeciated

A question was asked as to the importance of the Ubuntu Forums, well the help is priceless, and for anyone trying to migrate from Windows, it makes everything possible

best regards keith

---

### Post by catlett on 2006-06-03
Great!! It's always great to hear things went well. I mentioned the partitions because I have 15 (I'm a multi-boot bug) and I was shocked to see them all and with mount points.l have a bit of experience so I knew not to format the other partitions but I thought it a little irresponsible of the developers not to elaborate about formatting.
Actually they should make it clear on 2 points. First you have to format your linux partitions if you want to clear the previous data and install the filesystem. Second if you format the other partitions your data will be lost. Also they could have made it clear that you do not need to format those partitions to mount them.
These were the type of things that use to get me nervous and abort installatiions in the beginning of my linux use.
There were some good guides but I didn't find them and I went at it blind in the beginning (thank goodness IBM has a good rescue and recovery application). Now I try to post about things that weren't clear to me when I first installed.
Anyways, glad it went went well and remember "don't pay me back, pay it forward":D

---

