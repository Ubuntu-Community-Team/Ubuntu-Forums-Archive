---
title: "Partition Recommendations?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Danyl on 2007-04-23
Hi all

Its almost about to happen: I'm very close to devoting my entire PC experience to Linux and saying goodbye to Windows forever.

I'm just wondering what any experts out there can suggest by way of how I should partition by hard drive(s) to accomodate this.

I have 2 internal HD's, a 200gb and an 80gb. I read somewhere a while ago that recommended the best way to set up Ubuntu was with a series of partitions (one for root, one for the boot etc.) but having never done this I don't really know the best way to go. How many should I have?

FYI I plan on converting my entire CD collection to FLAC or OGG so I'm budgeting for approx. 80 gb worth of music (maybe more). But that aside, I shouldn't need any other large partitions.

So the big question, is it worthwhile partitiong? Will performance increase? If so, how should I allocate the space on my two hard drives?

---

### Post by nsleiman on 2007-04-23
i will tell you from my experience:
i have  800MB swap partition and i have a separated home partition where i put all my personal data. the /root will stay on another partition, so in case of a re-install you just hit the system partitioned part and not the personal and the music space.

i know people who don't even make a single partition. its your choice :)

---

### Post by RaZer0r on 2007-04-23
yes partitioning will increase preformance as not everything will be written to one hard drive.
best way to set this up could be:
/ : 25 gig of the 80 gig drive
/home : 30 gig of the 200 gig drive
/swap: 2 gig of the 80 gig drive (or the 200 gig drive, there is no increase with swap space)

the /boot, and other partitions are optional...
so you could for example use the free space of the 200 gig drive to partition to /media/data so that you'll never lose your downloads, data, music etc (whatever you put on it)
30 gig is plenty for the home drive, but you can use more of course.

grtz

---

### Post by Spr0k3t on 2007-04-23
This is what i would do.

Take your fastest drive and make that your root partition (generally 25GB is plenty for most).  Make sure you save 1.5 times your physical memory for a swap drive (so if you have 1GB mem, the swap partition is going to be 1.5GB).  Now you have the remaining space available.  I would probably put your /home/ drive mounted on the 200GB and the rest of your system on the 80GB even if the 80GB wasn't the faster choice.  Then, if you performed any upgrades, or had problems with the root drive, it's just a matter of dropping in a replacement and your /home/ partition is untouched.

---

### Post by indytim on 2007-04-23
I'll add one additional thing you may want to consider.  From my situation I also have 2 hd's ( 1-160G and 1-320G).  I have devoted the 160G to operating system(s) and related. This includes the /root, separate /home for each ops (excluding Windows :) ) and ONE swap.  I'm currently supporting Kununtu 6.10 & 7.04, Ubuntu 6.10 and Win2k.  I still have room for any other ops I may wish to test out etc.  

The 320 G has a NTFS partition for windows exclusive date files, a FAT32 partition for files I need to  share between windows and Linux, an ext 3 partition for media-type files, and ext3 partition dedicated to backup type of files.

This is just one perspective of how you may want to cut things up in your HD farm.  

Good Luck

p.s.  I always pre-partition everything before I install any ops (GParted Live).

---

### Post by Rinzwind on 2007-04-23
Laptop:

5 Gb /
1,7 Gb swap
33 Gb /home
100 Mb /data

/data contains scripts and files and is 1 partition I have backuped to gmail (just in case I format it ...) :) 
1. kickstart file for automated re-installation;
2. apt-get removes and installs of anything I don't like (gaim, ekiga, evolution) and do like (like VLC, XMMS, Streamtuner);
3. My own created wallpaper changer :lolflag: 
4. My wireless key including some fake digits and letters just to annoy ppl that do read it :KS So I don't have to retyp 128 random digits, letters and special characters :P

I am going to use this same setup for my PC when ever I want to go Feisty.

---

### Post by az on 2007-04-23
> **Danyl said:**
>  I read somewhere a while ago that recommended the best way to set up Ubuntu was with a series of partitions (one for root, one for the boot etc.) 


No way.

Maybe if you are running a server, or have specific needs (a very old motherboard that needs to have a boot partition so that the kernel image is always within the first few gigs of the hard drive space), but for desktop use it is best to have all-on-one partition.  There is less chance of you making a mistake during installation due to complexity.

As well, if you make one of your partitions too small, it can be a pain, if not impossible, to rearrange them.

There is no performance benefit to making seperate partitions.  If anything, your drive will run slower because you may increase seeking.  Also, if one of your partitions fills up, your performace will take a dive due to fragmentation.

Even a seperate home partition is a pain.  It is just easier to back things up the conventional way.

---

### Post by freebird54 on 2007-04-23
Speaking of backing up, I find it is nice to have a partition on the 'Data' Drive for holding image files of things I don't want to lose from the other drive.  Of course, it's nice to have backups on other media -but it is nice to just copy an image file over top of Windows when it F____ up!  Just an option for your consideration...

(not easy is it!) :D

---

### Post by mozetti on 2007-04-23
Well, I wouldn't listen to **az**, but I wouldn't worry about separate partitions for anything more than / and /home.

If you have 2 HDDs, you will get a slight (probably negligible) performance boost by having your /swap on the first partition of the 2nd hard drive. Basically, you 2nd hard drive can work on swapping while the operating system goes on it's regualar business. :)

For me, I have 9 partitions - / (root), /home, /music, /video, /photo, /data, /files, /workspace, and /swap. When I need/want to re-install Ubuntu, i just need to re-install root and set mount points for the rest. Easy-peasy.

---

### Post by rrsimm on 2007-04-23
Can someone point me to a good step-by-step tutorial for creating/using/managing additional partitions for an absolute Linux beginner?

---

### Post by mozetti on 2007-04-23
I cut my teeth in Linux trying to install Slackware. While it was too much for me to accomplish ~ 2 years ago, it wasn't for lack of good info.

This is from the Slack website, and gives you some basic info:
[http://www.slackware.com/install/partitions.php](http://www.slackware.com/install/partitions.php)

This is the tutorial I used to get Slack up and running.

[http://www.bitbenderforums.com/vb22/showthread.php?postid=311808](http://www.bitbenderforums.com/vb22/showthread.php?postid=311808)

It's very thorough and gives alot of info about partitioning. Start reading where it says > We need to type fdisk /dev/hda The instructions are for using **fdisk** in a pre-installation environment, which is a good way to really learn about partitioning. Otherwise, just use the partition manager on the Ubuntu Live CD or Gparted to create the partitions you want/need.

As I said in my post above, you really don't need more than /(root), /home, and /swap, but many people find good reasons for using multiple partitions.

---

### Post by freebird54 on 2007-04-23
Yipe!  I'll have to go looking for that myself.  I've been 'just doing it' since hard drives first got to 40 Mb (past the 32Mb limit for DOS).  Does it help if you just think of them as different drive letters?  (D:\ and E:\ and F:\)  :)

This link is a help for planning and creating....

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Hope that helps in the meantime!

---

### Post by antoz on 2007-04-23
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Tundro Walker on 2007-04-23
I started out dual-booting on 1 HDD, and it was good to have the following:[LIST]
[*]Partition 1 = WinXP (NTFS)
[*]Partition 2 = Shared (fat32 ... for shared content, EG mp3's)
[*]Partition 3 = Ubuntu (ext3)
[*]Partition 4 = Extended Partition (which holds sub-partitions)
[*]Partition 5 = Linux Swap (inside partition 4)[/LIST]As a Linux noob, I didn't go too ape with partitioning the drive.  But, I wanted to make sure I had a separate space to store things I wanted easily accessible, hence the SHARE FAT32 partition.  This worked out well, since it let me re-install Ubuntu a couple times without worrying about shuffling things around before doing so (IE: I didn't have to move mp3's and things off Ubuntu partition), and backups were easy since I basically just backed up the whole SHARE partition.

When I finally ditched Windows, I made the mistake of getting rid of my SHARE partition, too, so I had:[LIST]
[*]Partition 1 = Ubuntu Edgy (ext3)
[*]Partition 2 = Extended Partition (which holds sub-partitions)
[*] Partition 3 = Linux Swap (inside partition 2)[/LIST]However, after my Edgy installation got hosed from trying a Feisty upgrade (which I was anticipating), it would have been a drag having to salvage things off my hosed up partition 1 Ubuntu if I didn't back it all up first.

Even if you're only going with 1 Ubuntu installation, I'd recommend making 1 partition for bulk storage (mp3's, movies, etc), and another partition for the actual Ubuntu installation.  Like this.[LIST]
[*]Partition 1 = Share / Storage (fat32 or ext2 or ext3, to hold bulk of your files, like mp3's, movies, etc)
[*]Partition 2 = Ubuntu (ext)
[*]Partition 3 = Extended
[*]Partition 4 = Linux swap (inside partition 3)[/LIST]If you were going to use both HDD's for the Ubuntu installation (totally getting rid of Windows), I'd use do...[LIST]
[*]200gb (Share / Storage, formatted as fat32, or ext2 or ext3)
[*]80gb (Ubuntu Install and Extended / Linux Swap partitions)[/LIST]As long as you have that extra partition to store the bulk of your files you'd like to keep, I wouldn't get too anal about sub-partitioning things off more than that.

---

### Post by Danyl on 2007-04-23
Wow, thanks for all the replies guys.

Really appreciate it.

Your advice is invaluable as always. Thanks!

---

