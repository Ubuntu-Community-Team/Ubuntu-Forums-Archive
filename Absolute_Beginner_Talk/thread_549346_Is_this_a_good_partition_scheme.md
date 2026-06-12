---
title: "Is this a good partition scheme ?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by bolko7 on 2007-09-12
Hi all, I am getting ready to install Ubuntu on mine PC as only OS on it(few more days ), but i had a little problem i do not know is this a good disk partition scheme is safe and efficient.  I already read quit a bit on this subject but most of info is for Win + Lin and for one disk. I have 3 hard drives and i intend to have only Ubuntu. So pleas give me your opinion on this scheme and how much space i should give each Partition.

 Disk 1
/Boot 			[EXT3 (500mb)]
/ 			[ Ext3 (15g)]
Swap (2g)
/Tmp 			[ Ext3(5g)]
/Var 			[ Ext3(5g)]
/Home 			[ Ext3(10g)]
/Media/Manga 		[ Ext3(50g)]
/Media/Anime1 		[ Ext3(40g)]
/Media/Everything	[ Ext3(20g)]
Or 
Disk 1 
/Boot 			[EXT3 (500mb)]
/ 			[ Ext3 (10g)]
Swap (2g)
/Tmp 			[ Ext3(5g)]
/Var 			[ Ext3(5g)]
/Usr			[ Ext3(5g)]
/Home 			[ Ext3(10g)]
/Media/Manga 		[ Ext3(50g)]
/Media/Anime1 		[ Ext3(40g)]
/Media/Everything	[ Ext3(20g)]


 Disk 2
/Media/Anime2 		[ Ext3(80g)]
/Media/Movies		[ Ext3(30g)]
/Media/Music		[ Ext3(40g)]

 Disk 3
/Media/Games		 [ Ext3(20g)]

Thank you bolko 7

PS. Sorry for any mistakes.

---

### Post by slira on 2007-09-12
Hi
I'm not an expert, but it seems fine! 

I have
boot - 100mb - ext2
root - 5gb - ext3
swap - 2.250 mb (I have 1.5gb of Ram; 1,5 x Ram = swap) swap
home - 140 Gb - fat (because I want windows to read it)

and it works fine

good luck :)
slira

---

### Post by dwhitney67 on 2007-09-12
I would go with your first option for Disk1.  It would s*ck if you chose option 2 then found out later that the /usr partition was too small.

---

### Post by forestpixie on 2007-09-12
for disc 1 you would need to have an extended partition - and then logical volumes inside that. You can only have '4 partitions' I believe.

Also I don't know whether you would need to have a 15Gb / partition - depending of course on what you intend to install on top of the base install. I have 8Gb with 4Gb left.

---

### Post by asmoore82 on 2007-09-12
you don't get any performance gain from splitting the filesystem into partitions *on the same hard drive*
in fact, you most definitely shorten the life of your drive while maybe even slowing down your OS.

there are only 2 good reasons for an advanced partitioning scheme:

(1) by mounting partitions on *separate* drives as /usr,/var,/home you can increase performance.
(2) by keeping all personal data on a separate partition, you can easily re-install or switch OSes later on.

you need to strike up a balance between these 2 reasons without forcing a drive's read heads
to "tap dance" constantly because of too many partitions on a single drive.

the only sure fire advice I can give is to put a Swap partition at the *end* of every drive whilst
simultaneously keeping the largest bit of Swap on the same drive as the root partition;
so say 1X your RAM on the drive with the root partition and 1/2 your RAM on each of the other drives.
this does several things:
(1) slight performance increase
(2) may extend the life of drives in heavy swapping condidtions
(3) each drive has swap, therefore any drive isolated from the system will provide
some swap to a LiveCD

P.S. the worst thing that can ever be done in the future is
having to copy large amounts of data from *partition n* on *drive **x*** to *partition m* on *drive **x***;
However reading lots of data from *partition n* on *drive **x*** while simultaneously
writing lots of data to *partition m* on *drive **y*** is the greatest thing since sliced bread.

P.P.S. always place a swap partition at the end of the drive when possible because believe it or not,
a drive can actually seek from beginning to end *faster* that it can seek from beginning to middle.
This is true because seeking is not simply a function of velocity; it is instead the act of accelerating and deccelerating.

---

### Post by Tautoa on 2007-09-12
All sound advice, but I would add that, benchmarking shows that xfs tends to be quicker for reading/writing than Ext3, so you might want to use that instead.
Except, XFS file systems can't be read at boot, so you would need to leave your /boot partition as Ext3.

Apart from that, so long as they are big enough for your needs, and so long as you use logical partitions rather than primary, should be fine.

---

### Post by psusi on 2007-09-12
Is there a reason you are going nuts with so many partitions?  There is no reason to seperate /var from /, and you do not make a /tmp partition; files in there are stored in ram or swap.  Also /boot really only needs to be 100 MB or so.  Maybe 150 if you plan on keeping several kernels around.

---

### Post by asmoore82 on 2007-09-12
> **psusi said:**
> Is there a reason you are going nuts with so many partitions?  There is no reason to seperate /var from /, and **you do not make a /tmp partition; files in there are stored in ram or swap**.  Also /boot really only needs to be 100 MB or so.  Maybe 150 if you plan on keeping several kernels around.

this is true on some of the cutting edge distro's like gentoo and archlinux,
but on Ubuntu /tmp is an ordinary sticky directory;
because when it is a ramdisk to improve speed and "temporary-ness,"
programs that require more temp space than you have ramdisk space
(such as Unreal2004's installer and DVD-Video mastering programs)
will fail.

---

### Post by bolko7 on 2007-09-12
There is no express reason for so many partition anther then I read that making it that way make the PC safer and easier if something happens to one part of it. As i am new to Linux partition is Hard cuz there is not set rules for good way of doing it so i ask how to do it correctly. I want a safe and fast OS.
As for file system, I read that they are not so reliable as Ext3.

asmoore82 So it would be something like this ???

Disk 1
/Boot [EXT3 (500mb)]
/ [ Ext3 (15g)]
/Var [ Ext3(5g)]
/Home [ Ext3(10g)]
/Media/Anime1 [ Ext3 (95g)]
Swap (2g)

Disk 2
/Tmp [ Ext3(5g)]
/Media/Manga [ Ext3(50g)]
/Media/Movies-Anything [ Ext3(54g)]
/Media/Music [ Ext3(40g)]
Swap (1g)

Disk 3
/Media/Games [ Ext3(19g)]
Swap (1g)

---

### Post by psusi on 2007-09-12
> **asmoore82 said:**
> this is true on some of the cutting edge distro's like gentoo and archlinux,
but on Ubuntu /tmp is an ordinary sticky directory;
because when it is a ramdisk to improve speed and "temporary-ness,"
programs that require more temp space than you have ramdisk space
(such as Unreal2004's installer and DVD-Video mastering programs)
will fail.

No, /tmp is a tmpfs on Ubuntu; take a look at the output of df.  

Also /dev, /var/run, and /var/lock are tmpfs.

---

### Post by bolko7 on 2007-09-12
So How should i do it, cuz slowly i am getting lost how to do it. And i read at least 15 different Guides about this and it would seam it is all for nothing :(

---

### Post by psusi on 2007-09-12
150 MB for /boot ( and really you don't even need to do that if you don't feel like it )
everything else for /

Mount the second drive as one big partition in /media/drive2

---

### Post by az on 2007-09-12
> **psusi said:**
> 150 MB for /boot ( and really you don't even need to do that if you don't feel like it )
everything else for /

Mount the second drive as one big partition in /media/drive2

You don't even need a separate boot partition unless you are running an extremely old motherboard that can't read beyon the first gig of your hard disk.

All-on-one partition plus swap works and is the safest and most reliable.  If you have other hard drives around, you will easily be able to back up your data if you need to reinstall.  I do not recommend sharing a home partition between installs.

---

### Post by bolko7 on 2007-09-12
So something like this. 

Disk 1
/ [ Ext3 (20g)]
/Home [ Ext3(10g)]
/Media/Some Name [ Ext3 (Rest g)]
Swap (2g)

Disk 2
/Media/Some Name [ Ext3(rest g)]
Swap (1g)

Disk 3
/Media/Games [ Ext3(19g)]
Swap (1g)

To tell you the true i read every guide i could find and they all said something similar but in few there were written that making more partition for Linux makes the system safer ( I think i still think of Linux in Windows way, make it as safe as it can be cuz M$ is not going to help :D ). 
One more thing if I use different file system for everything beside "/" will it still work?(I will have to look up closer different files system, are they better and more imported are reliable)

---

### Post by asmoore82 on 2007-09-12
> **psusi said:**
> No, /tmp is a tmpfs on Ubuntu; take a look at the output of df.  

Also /dev, /var/run, and /var/lock are tmpfs.

it's funny you should tell me to use **df**, because on my system, /tmp is a tmpfs
because I added that entry to fstab by hand (former archlinux user here :p),
but on a fresher install of Edubuntu 7.04 ...

```
**asmoore@asmoore-laptop:~$** df -h | tail -n 1
tmpfs                 252M   16K  252M   1% /tmp
**asmoore@asmoore-laptop:~$** ssh eddy
asmoore@eddy's password: 
Linux eddy 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Sep 12 16:13:59 2007 from 10.200.1.35
*You will be successful in love.*
**asmoore@eddy:~$** df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   12G   56G  17% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   96K  506M   1% /proc/bus/usb
udev                  506M   96K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
**asmoore@eddy:~$**

```

---

### Post by rolnics on 2007-09-12
I like you read loads of guides, I went for separate a /boot / and /home, but I couldn't get grub working so I've just got my /home separate with / having 10Gb and /home 20Gb+

Other than that I'd go with you above partition setup

---

### Post by rsambuca on 2007-09-12
I agree with az and rolnics.  I see no real need to make your partitioning scheme so difficult.  10GB for /, 1 or 2GB for swap, rest for /home and you should be fine.

---

### Post by zetsumei on 2007-09-12
The way I did mine was...

/ 20gb ext3
/swap 2gb
/home rest of hdd (about 230gb)

---

### Post by asmoore82 on 2007-09-12
> **bolko7 said:**
> So something like this. 

Disk 1
/ [ Ext3 (20g)]
/Home [ Ext3(10g)]
/Media/Some Name [ Ext3 (Rest g)]
Swap (2g)

Disk 2
/Media/Some Name [ Ext3(rest g)]
Swap (1g)

Disk 3
/Media/Games [ Ext3(19g)]
Swap (1g)

That's 100 times better than where you started, but I would simplify
even more and take advantage of UNIX's ability to make mounts
"transparent" (i.e. leave the "Drive letter" (Removable storage) mindset behind)

[Disk 1]
/ (10 GB)
/usr/share/games (Rest GB)
Swap (2 GB)

[Disk 2] (smallest)
/home (19 GB)
Swap (1 GB)

[Disk 3]
/home/$username/somename (Rest GB)
Swap (1 GB)

and make sure you put custom games in /usr/share/games;
Synaptic and getdeb.net will already help you populate this location when appropriate.
take a peak at mine ...
```
~$ ls /usr/share/games/
applications  gridwars  irrlamb  vdrift       xmoto
fortunes      icons     locale   warzone2100  xpilot-ng

```

girdwars, irrlamb, vdrive, and xmoto are from getdeb.net
fortunes and xpilot are from stock Ubuntu apt repos
warzone2100 is from a deb package from wz2100.net

do you see the beauty of how they would end up on the same
"Games" partition together automagically without even knowing it?

And finally, at any time, the entire [Disk 1] could be trashed
or explode without you losing any important personal data.

---

### Post by rsambuca on 2007-09-12
Might I ask how much RAM you have?  It seems to me that 3 separate partitions of swap totalling 4GB is drastically more than you will ever need.

---

### Post by asmoore82 on 2007-09-12
> **rsambuca said:**
> Might I ask how much RAM you have?  It seems to me that 3 separate partitions of swap totalling 4GB is drastically more than you will ever need.

i could buy that too ... maybe 1/.5/.5 would be just as good as 2/1/1;
but then again, drive space seems to be at a luxury amount.

---

### Post by rsambuca on 2007-09-12
Personally, I have never even touched my swap, so I think it is a moot point anyways.

---

### Post by asmoore82 on 2007-09-12
> **rsambuca said:**
> Personally, I have never even touched my swap, so I think it is a moot point anyways.

i used to be able to say the same, but not anymore :cry:

GIMP and VirtualBox with only 512 MB or RAM will get you kneedeep in some Swap. :lol:

---

### Post by rsambuca on 2007-09-12
> **asmoore82 said:**
> i used to be able to say the same, but not anymore :cry:

GIMP and VirtualBox with only 512 MB or RAM will get you kneedeep in some Swap. :lol:

No doubt!  I don't think I would be running VirtualBox with that little amount of RAM.  Too slow!

---

### Post by bolko7 on 2007-09-12
This would be ok if not the fact that i do not play in many games (only EU2/RO) most of space take Anime and Manga plus music and Films and the smallest disk is the oldest(so i do not know if putting Home there is a good idea). But At last now I know exactly what to do :D.
Rsambuca I have 2g ram.

I Have to tell you all I am very grateful for all the help ppl here are giving me it is different then what i meet to this point with this topic on different web pages(most ppl there said Use search or google and nothing more, few even were extremely rude). So again Big THX to all. But now back to the topic.

I have 3 hard drives 2x160 and old 20

Ok i will try to make it more simple

Disk 1
/ [ Ext3 (20g)]( I want to keep here 20 g so I have enough space)
/Home/Some Name [ Ext3 (138 g)]
Swap (2g)

Disk 2
/Home/Some Name [ Ext3(rest g)]
Swap (1g)

Disk 3
/Home Ext3(19g)]
Swap (1g)

---

### Post by asmoore82 on 2007-09-12
> **rsambuca said:**
> No doubt!  I don't think I would be running VirtualBox with that little amount of RAM.  Too slow!

its a laptop from work so I can't really up the RAM ...

but i can run **either** GIMP **or** VBox smoothly; just **not both** :lolflag:.

---

### Post by psusi on 2007-09-12
I wouldn't bother using the 20 gig drive, and if the two 160s are the same model, set them up as a raid0.  Then your partitions on both disks will be:

150 MB /boot ext3
The rest / linux-raid

---

### Post by bolko7 on 2007-09-12
Sorry there is no way to set a good Raid cuz each Driver is a different. 

20g is a WDC WD200EB

Disk one is a Samsung SP1604N

And the last one is a SATA Seagate barracuda 160 (don't remember what model)

---

### Post by psusi on 2007-09-12
So?  They are close enough in size and speed aren't they?

---

### Post by bolko7 on 2007-09-12
I was always under impression that to set a good Raid(that will not kill  Hard drives) all Hard Drives should be the same. And i don't even know if it is possible to set one when one Hard Drive is on ATA and the second one is on SATA.(I was never interested in setting Raid cuz it always has some disadvantage).

---

### Post by psusi on 2007-09-13
Ideally yes, you want the drives to be the same make and model to get the best performance.  If they are about the same size and speed though, it's close enough.  If you stripe them you will get better performance, and won't have to worry about having to divide your files up between two different drives by hand, and possibly filling one up and not the other.

---

### Post by az on 2007-09-13
> **bolko7 said:**
> 
To tell you the true i read every guide i could find and they all said something similar but in few there were written that making more partition for Linux makes the system safer ( I think i still think of Linux in Windows way, make it as safe as it can be cuz M$ is not going to help :D ). 
One more thing if I use different file system for everything beside "/" will it still work?(I will have to look up closer different files system, are they better and more imported are reliable)

Certainly not on a desktop computer.  There are legitimate reasons to not put everything on one single partition when you are running a mail or web server, but those reasons don't apply to a desktop/workstation.

There are not even any legitimate reasons to have a separate home partition on a desktop.  Sure, you can do it if you want, but don't fool yourself into thinking that it's safer or better...

> **bolko7 said:**
> I was always under impression that to set a good Raid(that will not kill  Hard drives) all Hard Drives should be the same. And i don't even know if it is possible to set one when one Hard Drive is on ATA and the second one is on SATA.(I was never interested in setting Raid cuz it always has some disadvantage).

Linux software raid uses partitions, not physical drives.  You can have two different drives, but only use a portion of each for software raid - so long as the partitions are the same.

---

### Post by stimpack on 2007-09-13
> **az said:**
> 
There are not even any legitimate reasons to have a separate home partition on a desktop.  Sure, you can do it if you want, but don't fool yourself into thinking that it's safer or better...


Well it does have advantages that are significant. 

o Allows me to install a new distro whilst not affecting my /home. 
o Keeping /home on a different drive to / provides a speed-boost.

---

### Post by rfurman24 on 2007-09-13
I did not see this mentioned in the post anywhere but I would not use /media partions with Ubuntu. I used the do a /media in other distros and did the same when I first moved the Ubuntu only to find that Ubuntu actually uses /media for mounting devices. It was a little dance getting permissions set to write to that partition. I think I ended up editing fstab because I could not set permissions any other way. Now I just make a media folder in /home. It does not matter to me I just thought I would mention that.

---

### Post by bolko7 on 2007-09-13
I decided against Raid for now. I will see about it later on once i get a little more familiar with linux. 
As for the mine topic i come up with something like this.

Disk 1
/ [ Ext3 (15g)]
/Home/$username/Media/Some Name [ Ext3 (133 g)]
Swap (2g)

Disk 2
/Home [ Ext3 (15g)]
/Home/$username/Media/Some Name [ Ext3(134 g)]
Swap (1g)

Disk 3
/usr/share/games Ext3(19g)]
Swap (1g)

Can this do or should i change something??

---

### Post by psusi on 2007-09-13
Again, there is no reason to have all those partitions.  Just put / and swap on disk 1, and /home and swap on disk 2.  Don't even bother using the 20 gig drive as you will end up filling it up and it is slow.  If you want to have it around anyhow, just mount it in /media.  Don't put swap on it.  

As for /media, all that means is that it will show up on the desktop.

---

### Post by rsambuca on 2007-09-13
I am totally with psusi on this one.  Scrap all the unnecessary swap partitions.  With your 2GB ram, unless you are doing something well beyond the ordinary, you will never touch them.  I never have seen the need for the physical partitioning of your media this way.  What if later you need more space for one particular media type?

---

### Post by rsambuca on 2007-09-13
> **stimpack said:**
> Well it does have advantages that are significant. 

o Allows me to install a new distro whilst not affecting my /home. 
o Keeping /home on a different drive to / provides a speed-boost.

A significant speed boost?  May I ask how much of a speed boost you will see?

---

### Post by bolko7 on 2007-09-13
Disk 1
/ [ Ext3 (All g)]
Swap (2g)

Disk 2
/Home [ Ext3 (all g)]


Disk 3
/Home/username/Archives [ Ext3 (all g) ] (mostle txt staff, info and archives data. Like Contact list, Ftp list ect. NO programs or anything what is used)

Psusi something like this?? Ok this is absolutely noob question but will giving most of space for "/" prevents me from using it in /Home (In windows it would)

---

### Post by psusi on 2007-09-13
Yes, that's a fine setup, but I would put the third drive in /media instead of /home/username so it shows up on the desktop.

---

