---
title: "A touch of partitioning advice"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Rotting on 2008-03-13
I need just a touch of partitioning advice, as I seem to have screwed up (not TOOO royally) in my last few projects concerning gparted.

So, here's my situation and plan. I have a 750GB HDD. I want Vista, Ubuntu, OpenSUSE and Solaris in different partitions.My "main" partitions (i.e., the ones that I'll be using 95% of the time) will be Vista and Ubuntu. I just want OpenSUSE and Solaris on there to mess around with them and see how they work. Now, I guess the monster share of the HDD should go to Vista, since that's where all the huge games, etc. will be going. 

So, I was thinking about 500GB to Vista, 150 to Ubuntu, and 50 each to OpenSUSE and Solaris. (These aren't set in stone, so if you have a better idea, let me know!) SO, what is the best way to accomplish this? Step-by-step (in a general sense--you don't need to say "click here, click there" but more like "Make an NTFS partition here and put a ext3 in an extended partition, etc etc etc.) would be nice. 
Also, is there an easy way of making an EXACT copy of a partition to copy from one HDD to another? (I want to move my current Vista installation and Ubuntu installation from a smaller drive to this new one)>

Thanks a lot for your help.

---

### Post by tompickles on 2008-03-13
Not sure about the copying exact partitions - think you need a commercial tool like partition magic.... not sure though.

You know you can only have 4 primary partitions on one HDD, so id create an NTFS and then 3 extended partitions. one would house ubuntu / and your general /home for use by all distros and a chunk os swap. then second for suse / and forth for solaris /.... but not actually sure if thsid will work. By having one /home partition you can access it from all distros. and, you only need one swap parition as you will only be running each distro independantly from the other. So, yeh. Maybe another soution is again 4 partitions, vista, /home, swap, and the forth is extended for all the / of the distros. Might work better. remeber wiht shared /home partitions, use different user names to prevent different versions of apps overwriting config data in there form other distros..... maybe that helps, or is totally wrong.. maybe other people have more ideas/corrections?

---

### Post by Rotting on 2008-03-13
Do you know what the practical differences in the two options you suggested are? Is one better for one type of use the other for another?

Thanks

---

### Post by forestpixie on 2008-03-13
Pretty sure you can only have 1 extended partition on a hdd - but it can have a *lot* of logicals within it

Perhaps
Vista -NTFS
Swap 
Data - shared
Extended 
Logical - Ubuntu
Logical - Suse
Logical - Solaris

Let each have it's own /home rather than a common one, but use the shared partition for things you're likely to need in more than one

---

### Post by tompickles on 2008-03-13
not really sure on the practicallities, but looking above at the previous post, that seems a good sugggestion. I think that having /home as a primary partition and again swap would just make things simpler. Having a shared /home folder has few disadvantages other than clashes between distros which is a biggy!, so long as you mount it properly with each install of the OS, and if you use different usernames, ie rotting-ubuntu, rotting-suse and rotting-solaris which will prevent this clashing. Also, a slightly more filldy option, is............ have rotten as your user name on all three for example, but have the suse home folder for rotting at /home/rotting-suse etc. checkign with Linux Format openSUSE can do it all in User Management. With Ubuntu, open a console, then open user manager, select your user and properties, advanced and change home directory. then, sudo mv /home/rotton /home/rotten-ubuntu   then log in and out....... but maybe this isnt the best idea, and having seperate /home will not cause this problem at all. You will defiatly need just one swap. but how you play the rest, im not sure. its a complicated issue.

I think the simplest is:

Vista
Swap
/home
Extended-
/ ubuntu
/ suse
/ solaris

and use different user names in each of the distros

---

### Post by Duck2006 on 2008-03-13
Let vista make  it's own partition and leave the rest blank. Then look at one of the post in this thread to get a good idea as to what way to split the drive up with. Round 10 to 20Gb ( may be to much) for each linux you install.

---

### Post by the-edmeister on 2008-03-15
[quote="Rotting"]Also, is there an easy way of making an EXACT copy of a partition to copy from one HDD to another? (I want to move my current Vista installation and Ubuntu installation from a smaller drive to this new one)>[/quote] There are a number of programs to "clone" Windows partitions. I have used an old version of Ghost PE, from Norton System Tools 2000, for the last 8 years (on a floppy disk - cloning is best done without the OS you are cloning booted up) to clone Windows partitions, the main limitation with Ghost is that when you restore to a larger partition that what you "ghosted" from you're only gonna have the size you actually "ghosted" - the rest of that partition is wasted. I'm not sure if other partitioning 'cloning' programs work that way, but it is something to look into.
Cloning of a Linux partition - I have no idea, I am new to Linux, but I have done extensive research into partitioning drives for installing various favors of Linux to try out, along with Windows 2000. I am currently triple booting W2K, Ubuntu 7.10, and OpenSUSE 10.3, for the last couple of weeks.

[quote="Rotting"]I have a 750GB HDD. I want Vista, Ubuntu, OpenSUSE and Solaris in different partitions. ... Now, I guess the monster share of the HDD should go to Vista, since that's where all the huge games, etc. will be going.[/quote] IMO, the bulk of that 750Gb should be your "data" partition (like maybe 500Gb to 600Gb) and formatted to FAT32 so the OSs's that don't support NTFS can use that partition. The most important files on your computer are your "data" files, having them in one central location (away from the Windoze "My Documents" location) is the safest way to run Windows (IMHO) - plus it is a lot easier to 'burn' a backup when they are all on the same partition.

Figure out what size your Vista installation is now using and plan for the same size partition on the new drive (once you start using Linux you probably won't have much use for Vista for much longer, except for gaming and for the few proggies you can't find suitable Linux replacements for).
IMO, much more than 10Gb per Linux flavor would be a waste, with all your data residing on its' own partition there isn't much besides configuration files and program files to take up space on your OS partitions.

Now, when it comes to configuring your Linux installations, my thoughts are to have separate **/** (root), **/**home, and **/**swap partitions. As far as the specific sizes of each of those partitions, I am not even gonna venture an opinion, I'll leave that to those users who have used Linux for a lot longer than I have.

Just my thoughts, Ed

---

