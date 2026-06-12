---
title: "Partitioning questions"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by i_am_samus on 2007-06-19
I've read the other documentation on partition Ubuntu onto my Dell PC (which obviously runs Windows)

However, in one of the documents I was reading, it mentioned that if you selected the drive you want to partition, it allows you to, graphically, determine how much of the drive you want to partition.

Here's my problem:

First off, I have one 40 GB hard drive. 75% of which is full. I want to partition maybe 5 GB of that free space. Also note that I know next to nothing about partitioning. So, I decide to select the option of "choose largest continuous free space." It says that I do not have enough space to do so, so I am left with the option of partitioning my whole hard drive.

I also want to keep Windows XP still on my computer, as well as preserve my original data.

My question is, will this wipe my data clear? Or will it just find different spots among my HDD to partition on. Also, what would be a good way to dual boot without formatting...

Any and all help is much appreciated.

Thanks :)

---

### Post by floke on 2007-06-19
It will wipe all your data yes.
You cannot dual-boot without formatting unless you can boot from a usb and install Linux there.
5Gs really is no way near enough for an install. I would say 10G minimum.
You need to clear some of the junk off your drive. IMPORTANT - derag and scandisc first!
Then partition and install.

Hope this helps.

---

### Post by i_am_samus on 2007-06-19
So are you saying that if I cleared enough space, it would let me partition some of the Hard drive and not wipe my data out?

Or do I, under any circumstances, have to format my HDD, and backup my information..

---

### Post by mikewhatever on 2007-06-19
Rather then partitioning during the installation, I'd suggest using the partition manager of the Live CD before the installation. You can find it under System>Administrations. To be sure, it is the same tool, but it looks different. All you have to do is drag the right end of the selected partition to the left. Make sure to leave some space for Windows, defragment before resizing, and run the CHKDSK check in Windows.

---

### Post by KIAaze on 2007-06-19
Mmh, I have Debian running perfectly on 5GB. (after install, it only takes about 2GB).
I don't remember how much space Ubuntu occupied after a fresh install, but I wouldn't say that it's impossible on 5GB (well 4GB, if you leave 1GB for swap).

Of course, the problem is that you'll be limited in installing all the great programs available for Ubuntu. ^^

I have always partitioned first with the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and then installed Ubuntu. Maybe you should try it too, to see if it lets you partition at least.

[edit]
Or as previous poster just suggested:
> Rather then partitioning during the installation, I'd suggest using the partition manager of the Live CD before the installation.
That should be about the same thing as using the GParted LiveCD. ;)
[/edit]

Eventually, you could try out other smaller GNU/Linux distros like Damn Small Linux, Puppy Linux, etc...
But they may be less user-friendly of course.

> IMPORTANT - defrag and scandisc first!
Then partition and install.

And I would also add: **Back up important data first.**
**** shouldn't happen, but **** can happen. You never know. ^^

---

### Post by floke on 2007-06-19
Oh yes - good point!
Also - dont trust the partitioner on the liveCD - use the alternative installer - its FAR safer!

---

### Post by bodhi.zazen on 2007-06-19
1. Start in windows.
[list][*]Delete/remove what you can or do not need.[*]Defragment X2[*]BACKUP any mission-critical data[/list]


UNDERSTAND partitioning terminology so as not to overwrite windows :)


2. Boot the Ubuntu CD and re-partition with gparted.
[list][*]Basic partitioning : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[*]Gparted how-to : [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
[*]You can install Ubuntu to 5 Gb, but you will run out of space soon.
[*]You also need swap (ram X2, max 1 Gb or = ram if you hibernate[/list]


3. Install Ubuntu
[list][*][http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)[/list]

If you do this you will have Ubutnu, very low risk of data loss (but not no risk).

hth

---

### Post by KIAaze on 2007-06-19
> **Steve.K said:**
> Oh yes - good point!
Also - dont trust the partitioner on the liveCD - use the alternative installer - its FAR safer!

??
I don't understand.
I only installed Ubuntu once so I don't really remember, but what do you mean by "alternative installer"?
The partitioner on the LiveCD is GParted, no?
Is it less safe to use GParted than to use the partitioning during the installation phase or what?
I mean, I never had any problems with GParted. In fact, I had fantastic experiences with it for playing with my partitions. :)

Just curious for when I'll have to reinstall Ubuntu...

---

### Post by floke on 2007-06-19
For me Gparted on LiveCD of Edgy works fine, for Feisty I get cock-ups all over the shop. It keeps mounting partitions in the middle of the process then saying it can't finish the process because the partition is mounted (wtf!!). I know that this has buggered things up for a few people. Trying to partition my external HDD I had to keep unmounting it at every turn. I have never had any trouble with the alternate installer, since it doesn't mount the partitions. Maybe you;ll be fine with it. And maybe its just me. But that's my experience.

---

### Post by KIAaze on 2007-06-19
Maybe it's because the Ubuntu LiveCD mounts partitions automatically (so that you can have a nice Live experience).
The simple GParted LiveCD probably doesn't do that since I never had the problems you mention.

---

### Post by i_am_samus on 2007-06-19
Alright, so I feel like I'm getting this partitioning stuff...I hope I am not slow at this xD. 

Also, sorry it took so long, I got busy. Now. I have Gparted up, and here's what I have:

[IMG]http://i70.photobucket.com/albums/i86/gamerchic4/Screenshot--dev-sda-GParted.png[/IMG]

Any thoughts on how I can partition? I really don't want to mess anything up since me and my dad use the same computer, and he also has some valuable information saved.

---

### Post by floke on 2007-06-19
First - BACKUP YOUR DAD'S DATA!!
2nd - problem: you can only have 4 primary partitions on a disc. Linux needs 2 (system+swap). And you already have 3!
What's sda1? Can you delete it?

---

### Post by KIAaze on 2007-06-19
Your disk is strange. Is this really your current setup?
Why do you have 31MB of FAT16 at the beginning, 4GB FAT32 and 8MB unallocated at the end?
Do you know what's on each of these partitions?

> **Steve.K said:**
> 
2nd - problem: you can only have 4 primary partitions on a disc. Linux needs 2 (system+swap). And you already have 3!

That's not a problem. He can create an extended partition and put as many logical partitions in it as he wants! :D
([well, almost anyway (15 partitions total on an SCSI disk and 63 total on an IDE disk)]("http://tldp.org/HOWTO/Partition/partition-types.html#logical"))

Ubuntu, as well as any other GNU/Linux distro, can be installed on a logical partition without any problems.
The swap partition can also be on a logical partition.

Here's what a disk with an extended partition looks like:
1)primary
2)primary
3)primary
4)extended:
-logical 1
-logical 2
-logical 3
-...

You can easily try it out with GParted to better understand it.
The good thing about GParted is that as long as you don't click "apply" nothing is done. So there's no risk in trying different configurations to see what they look like.

_Tip:_
Altough you can chain a lot of operations with GParted, try not to chain too many since it can take quite some time, especially when moving partitions or resizing "to the left".
Avoid doing and undoing operations. (so once you have visualized your future setup, try to obtain it with the least steps possible)

---

### Post by floke on 2007-06-19
Yes but he hasn't got a lot of free space. So - well I was thinking delete sda1 and then set up the system - but actually you're right - it can all go in an extended - either way though there's no room - you need to leave a few gigs left for Windows - which leaves around 5Gs for ubuntu - which isn't really enough.

---

### Post by i_am_samus on 2007-06-19
Yeah that is my actual partitionings. Like I said before, I am a total n00b at this, I would have never known that it was an odd setup. Is it a Dell thing, I'm not particularly fond of Dell...

Also, I'm going to have my dad backup his stuff because I do not know where he keeps all his important data. But if I get him to do that, he'd be too lazy. I think, since I am almost out of HDD space anyways, I'll wait till I run out and I can convince my dad to buy a new Hard Drive.

For future reference, a new Hard drive is blank, so I can partition all of Ubuntu on it, right?

Once again, all that helped, you helped me very much. Thank you so much. :)

---

### Post by KIAaze on 2007-06-19
I heard that Dell offers something called "media center". It's probably because of that that you have such a strange setup.

You have about 24GB free on /dev/sda2 (which is obviously your windows partition).
So one possibility would be to reduce the size of /dev/sda2 **(defragment it first)** and put another primary partition for Ubuntu in the freed space.
24GB is more than enough for Ubuntu.
If you want you could even split it into two logical partitions: one for /home and one for the Ubuntu OS. ;)

You might also move /dev/sda3 further to the right to free even more space for Ubuntu, but I don't know if this will affect the Dell media center.

cf [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning") for further newbie-friendly reading on the subject.

---

### Post by i_am_samus on 2007-06-19
That was very helpful, thank you so much :)

Of course, I'm open to any and all suggestions, unless I have the problem solved.

---

### Post by st33med on 2007-06-19
Also, in Windows, do you have a backup drive? If so, the backup drive is the FAT-32 system. 


[SIZE="5"]BUT WHATEVER YOU  DO, DO NOT DELETE THAT FIRST PARTITION!!![/SIZE]


That is for Dell's recovery thing. I'd advise not to erase it because things may go screwy,

---

### Post by mikewhatever on 2007-06-20
> You have about 24GB free on /dev/sda2 (which is obviously your windows partition)
KIAaze, look at the screenshot. The 24 GB you somehow saw as free are in the 'used' column. It also says 8.18 is unused.
> So one possibility would be to reduce the size of /dev/sda2 (defragment it first) and put another primary partition for Ubuntu in the freed space.

i_am_samus, do not do this. If you make Ubuntu root a primary partition, you would not be able to create the swap partition, because of the four primary partitions limit. If you do decide to install, create an extended partition out of unallocated space, and then make all the partitions you create logical.

---

### Post by KIAaze on 2007-06-20
edit: posting error

---

### Post by KIAaze on 2007-06-20
Oops, yes you're right. I misread and forgot the swap. Sorry. :oops:
But 8GB is still enough to put in Ubuntu+swap.

---

### Post by floke on 2007-06-20
It is, but it leaves no more room for Windows.
Its a bit tight. I'd remove some stuff from the NTFS partition first.

---

### Post by i_am_samus on 2007-06-20
Ok, so I feel like I kinda get the partitioning thing, however, I am not that confident yet. In the end, I think I will wait till I buy a new hard drive. I deleted a bunch of stuff right before checking out Gpart...and it looks like all my necessary stuff cannot be deleted yet they take up a lot of room. This computer is only about 3 years old, and a 40 GB hard drive is kinda small. I only keep what I use on it, delete everything else.

So once again, thank you all. This helped so much :)

---

