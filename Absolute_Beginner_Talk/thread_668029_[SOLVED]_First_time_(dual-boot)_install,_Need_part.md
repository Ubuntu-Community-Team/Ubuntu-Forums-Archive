---
title: "[SOLVED] First time (dual-boot) install, Need partition help."
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-15
I've been looking around the forum but haven't gotten a solid answer that helps me with what I'm after.  I hope someone can shed some light on this for me.

I have a single 80gb drive with Windows XP installed onto a 40gb partition at the beginning of the drive.  I went to install Ubuntu and once I get to the partition choices I start to get lost.  Basically I don't want *anything* done to the existing 40 gigs where XP resides.  My intention was to install Ubuntu (7.10) into the remainder empty space (approximately 35gb, give or take).

I was going to go with the "guided largest unused space" (or whatever it's called), but then it mentioned something about creating multiple partitions with sizes I wasn't expeting with IDs that didn't seem to make sense (hda2 and hda5?).  I thought I would swing by here to see what anyone recommended.

Again, I have a 40gb XP partition at the beginning of the drive and I've set aside the remainder of the space (currently unpartitioned) for Ubuntu.

Side question:  What's a good amount of space for a system partition for Ubuntu?

---

### Post by Rocket2DMn on 2008-01-15
When you install you will need a root partition and a swap partition; a /home partition is optional (probably won't want it with 35 gigs total).  SWAP should be 1.5-2 times your RAM amount.
hda* are separate partitions on the physical drive that linux calls hda.  A second hard drive would be hdb.
Ubuntu can fit on a relatively small amount of space, but you might as well use the 35 GB.  It all really depends on how much media you keep on the drive.  The Ubuntu install uses well under 10 GB I believe (probably closer to 5).

Just be sure you don't wipe out windows, I always recommend keeping complete and up to date backups, regardless of the OS.

---

### Post by c0met on 2008-01-15
Hi Toasty,

When I install Ubuntu, I always set my drives up beforehand using the partition editor on the  LiveCD. To do this, just boot up from the LiveCD and then go to **[COLOR="Purple"]System >> Administration[/COLOR]** and you'll see the Partition Editor. When you run this, it will show your hard drive and its partitions. The partitions will probably be called[COLOR="DarkRed"]** /dev/hda1**[/COLOR] and **[COLOR="DarkRed"]/dev/hda2[/COLOR]** (it might be that you have[COLOR="DarkRed"]** sda**[/COLOR] instead of[COLOR="DarkRed"]** hda**[/COLOR]).

Presumably Windows is on the hda1 partition. If that is so, there should be a shaded section on the left of that partition. If hda2 is empty, it should simply be a clear partition.

What you will need to do is to use the partition editor to create 3 partitions within the partition you have set aside for Ubuntu. To do this...
[LIST]
[*]right click on the partition (presumbly /dev/hda2 or /dev/sda2)
[*]select "new" partition
[*]make it (say) 10 gigs big: this will late become the "/" partition and will store the operating system files
[*]choose the format to be EXT3
[/LIST]
You should now have 30 gigs remaining. (As a note, I set the mount points during the install process). At this stage, you can click "apply" if you want to go ahead and create the 10 gig partition. If the Partition Editor shuts down after you have clicked "apply", simply restart it. It's ok. 

Continuing on...
[LIST]
[*]right click on the remaining 30 gig parition
[*]create a new partition that's around 28 - 29 gig big
[*]format this to EXT3
[/LIST]
Lastly...
[LIST]
[*]right click on the remaining 1.5 (or so) partition
[*]choose "new"
[*]format it to a swap file
[/LIST]
That's the partitions set up.

Now install Ubuntu. When you get to the partitioning section of the installation, choose [COLOR="DarkRed"]**MANUAL**[/COLOR]. You will see all the partitions you have made. For the 10 gig one, choose to edit it and set it's mount point to "/". For the 28 (or so) gig one, edit it and set its mount point to /home. You will also need to put a checkmark in the "format" option of the "/" partition.

That's it. You can now continue with the installation. A word of advice. Install the program while your internet connection is open. When you get to around 82%, the installation will seem like it has frozen, it hasn't, it's simply downloading repository files from the internet.

Hope that helps.

---

### Post by oni5115 on 2008-01-15
I'd suggest around 10 Gb for /  
1Gb-2Gb for swap. depending on ram.  (With 2 Gb of ram I have yet to see my swap go past 0 on Conky!)
the rest for /home

It just makes upgrades and installations a little smoother if you can keep your settings and docs in one location.  (Besides, if you get the etx2/3 driver for windows... you can actually use /home for your documents and share it between both OS'es.  (It seems to be working nicely for me so far, for the rare occasions I actually want/need to go into windows.)

Anyways, I set mine up as 10 Gb win, 10 Gb  root, 2 Gb swap, and the rest as home.  (but I was also doing a fresh install on a new drive and had all my data and docs on an external HD, so I didn't need to worry about them.)

as an fyi, Ubuntu takes up 4 Gb at the moment, with gnome, the kdepim package, audacity, and some photo apps.  It took about 3.3 Gb or so for a default install.  I use 10 Gb so that I have plenty of space to grow.

My clean and upraded windows takes up about 5 Gb atm.  so it works out well.  Probably more info that you really need, but might be useful if you ever plan on shrinking / reinstalling windows some day.

---

### Post by toastysquirrel on 2008-01-15
Awesome guys, thanks!

Okay, so at this point it seems like you're saying to set aside (roughly):
10gb for the "/" (where the OS and junk goes)
1.5-2.5 x RAM for the swap
Remainder for "/home" which is where settings and data is stored (??).

Let me throw another somethin-somethin' your way, just to see if it changes anything.  I have a separate (physical) drive of 160GB, currently formatted as NTFS.  Ubuntu Live sees it, no problem.  This drive is where I keep all of my data (non OS/programs/etc).  Does this in anyway change your recommendations for having different partitions for / and for /home?

Thanks guys, I freakin' love Ubuntu, I actually used it *all day* long, didn't even boot into XP once.

:)

---

### Post by Rocket2DMn on 2008-01-15
I personally don't think you need a separate home partition.  If you use a backup program and you end up having or wanting to reinstall the OS (not likely!), you can restore the stuff you need, including your home folder.  If you're interested, I use a program called sbackup.
However, it's your system, so it's your call.  Everybody has their own preferences.
I would keep your other hard drive for data, you can read/write ntfs with the ntfs-3g driver.
Also, you don't need 2.5x your RAM for swap, 2 is that max, you could get away with 1.  I'd say go with 1.5x for a happy medium.
Welcome to Ubuntu!

---

### Post by c0met on 2008-01-15
Toasty,

As Rocket has said, your 160 GB drive will be automatically read/write accessible under Ubuntu. There is nothing that you need to change. For it's OS, Linux requires a specific format which is why I mentioned EXT3 (this is one of the formats). For your interest, you will never have to defrag the EXT3 formatted drives because they maintain themselves. Makes you wonder why NTFS does not!

As Rocket has pointed out, some people don't have a separate /home directory and some people do. It's probably a 50/50 call. I chose to have a separate /home because each time you re-install Ubuntu, the / drive will be formatted as part of the preparation. Having a separate /home partition means that this partition will escape formatting. Since program settings are usually under /home, this means that if you reinstall the OS and the programs you originally had on, many of your settings are good to go :)

This turned out to be a good advantage for me because I have re-installed Ubuntu 3 times since I started playing with it a month ago. You see, I like playing around in areas that can mess the system up ;) and the separate /home partition has proven to be very useful. 

All the best!

---

### Post by toastysquirrel on 2008-01-15
Man, I feel liberated this morning.  Fresh out of bed I swung by the forum to reread your guys detailed input on the install and off it went.  I currently just booted into XP (post Ubuntu install) to make sure it still works, and it does (no surprise).  Now time to restart for my first *real* boot into Ubuntu.  I went with a partition split of:

22gb - /
12gb - /home
2.25gb - swap

Mainly because I'm just learning the OS and I know I'll be making *tons* of experimental changes and I'd prefer my settings and whatnot, not get wiped out during my anticipated reloads.

Thanks a bucket-load guys!

---

### Post by talkeetnaweb on 2008-01-15
I just did the same thing and found the partitioner does the opposite of what it says it is going to do. I selected the first option and moved the slider to the left to "make the new partition 20 gig." (I have 80 gig total.) Instead, it made the old partition (windows xp) 20 gig and ubuntu 7.10 60 gig and now I'm trying to figure out how to fix it (problem solved, see below) so I have some space in windows.

So I guess the answer for you is to select the first (default) option and move the slider to give the size you want XP to be, i.e. 40 gig, as the new partition size. Ubuntu has made great strides in the installation process over the past few releases. Hopefully they will make the partitioner communicate with the user more clearly for the next release.

P.S. Thanks to c0met's detailed reply to this thread 11 hours ago, I was able to boot from the cd and use GParted to make the partitions the right size.

---

### Post by logos34 on 2008-01-15
> **talkeetnaweb said:**
> I just did the same thing and found the partitioner does the opposite of what it says it is going to do. I selected the first option and moved the slider to the left to "make the new partition 20 gig." (I have 80 gig total.) Instead, it made the old partition (windows xp) 20 gig and ubuntu 7.10 60 gig and now I'm trying to figure out how to fix it so I have some space in windows.

So I guess the answer for you is to select the first (default) option and move the slider to give the size you want XP to be, i.e. 40 gig, as the new partition size. Ubuntu has made great strides in the installation process over the past few releases. Hopefully they will make the partitioner communicate with the user more clearly for the next release.

yeah, that causes more confusion...the devs really need to change that.  "New partition size"--semantically, you can read it either as the 'new size of the partition after resizing', OR 'size of the new partition'.

---

### Post by Sladi on 2008-01-16
Hi! 
Where does Ubuntu install application files to? 
Can I use a partition for that (or even a specific directory)? 

I'd like to use a small OS partition and have the rest for program files, game files and other files. Is this possible? 

Thanks!

---

### Post by c0met on 2008-01-16
You can see where application files are installed as follows[LIST]
[*]opening the Synaptic Package Manager
[*]find the installed program of interest
[*]right click on that name and select "Properties"
[*]click on the "installed files" tab
[/LIST]
As you will see, components often get installed in hidden directories on the home drive (these are directories with a . in front - e.g. .mozilla). You'll also see that many components are also stored in directories off the / directory. In other words, it's unusual for there to be a single location for a program to be installed.

---

### Post by Byakira on 2008-01-17
Hey guys. I have a problem

I dont think the Live CD see's my Disk. It just wont show up and takes ages when I try and do step 5 of the installation (Partitioning)

[ATTACH]56685[/ATTACH]

Thats all I see...ever

---

### Post by Rocket2DMn on 2008-01-17
Can you see the disk with the following command?  Post the output if you're unsure:
```
fdisk -l
```
I don't think you need to sudo that command from the LiveCD, but you might need to.  Try both.
Otherwise, you may need to try the alternate install cd which doesn't have a live session. You can download it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by selecting the Alternate Install CD checkbox at the bottom.  This fixes a lot of problems that people have with the LiveCD, and I've never heard anybody complain about the alternate cd, so it should be rather intuitive.

---

### Post by c0met on 2008-01-17
Hi Byakira,

Another approach might be as follows. Before you start the install process, go to System >> Administration and start the Partition Editor (It's GParted). The graphical interface of this could make it easier to see your drives.

---

