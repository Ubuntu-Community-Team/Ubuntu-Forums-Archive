---
title: "Just running live CD"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by gbswales on 2007-08-07
I am running the latest 7. something Ubuntu from live CD - I had tried it a long time ago and been dissapointed that I needed to make so many manual interventions to get everything running - this time it was quite different and it found my network, got emai and the web and access to all my files up and running in no time. Great I thought now is the time to set up a dual boot system as I can easily spare about 40 gb of my windows hard drive - PROBLEM is no matter which way I seem to go through it I end up with a screen which is telling me it is going to lose all the data on my hard drive - I tend to trust messages like that!!!

I have been looking around for which things to tick that will ensure that it just repartitions the disc and keeps my windows installation intact (I cant avoid windows as I need it for some windows only apps and anyway I just want to test ubuntu in dual boot for now)  I do hope that I dont have to go back to pre-preparing the drive like you used to have to do - I got the impression that this distro (see I am learning the lingo :)) would handle everything safely and automatically without me having to mess around (well apart from backing up data first of course)

I also want for now to keep all my data files on the windows partition - so that "my documents" are all safely together etc. It looks as if this should be possible from the disc version.

I looked at the help file that comes with the distro and cant find anything about installation from the live cd - how frustrating.  It's basic stuff like this that make so many people give up at the first hurdle.

Anyway if someone can help before I have to close the CD version down and start again I really would appreciate it.

---

### Post by Nike T on 2007-08-07
Did you defrag the disk yet?  Back up all your important info?  You could use Gparted, that will not delete everything on the windows partitions.

---

### Post by gbswales on 2007-08-07
Now you have lost me, defrag I understand but I have software that does this regularly already, and my data is backed up nightly.  I thought that the whole dual boot thing could now be set up automatically from the install icon on the desktop? Is that not the case?

---

### Post by Rocket2DMn on 2007-08-07
Although I haven't tried, I'm skeptical of resizing older NTFS partitions.  As the data gets spread out from Windows, even defragging won't necessarily move everything out of the way so space can be set aside for Ubuntu.
My suggestion is to back up all your data and start fresh.  If you choose this option, you should install Windows first on however much space you want to give it, leaving the rest of the disk as unformatted space.  Then when you install Ubuntu you can put it there (no partition resizing necessary).  If you give Windows the whole drive when you reinstall it, after defragging you should have no trouble resizing the partition from the Ubuntu LiveCD (since there is essentially nothing on the drive yet) and giving Ubuntu however much you want.

However, you can try to resize from what you have now, it technically should work, but I can't offer guarantees.  If you try this and it breaks Windows, you can reinstall Windows and restore your backups.

---

### Post by annda on 2007-08-07
the installer will ask you about partitioning options, just DON'T choose 'use entire disk' - it will erase everything. use the guided partitioning to set the partition sizes.

---

### Post by gbswales on 2007-08-07
file:///home/ubuntu/Desktop/Screenshot.png

This shows the options I get in the partitioner - none of which seem to be re-partitioning keeping existing data

Treat me like a novice 
1) I want to intsall ubunto from this live CD on the same drive as windows
2) I want to leave my windows intact and have the option on boot up to choose which system
3) I want next to no manual intervention - other than answering simple questions

so what do I select?

---

### Post by Nike T on 2007-08-07
I think you should partition manually using gparted, gparted is a partitioning program that can be found under system, administative stuff, it's called gnome partitions editor or something like that.

---

### Post by annda on 2007-08-07
are your options different than those?
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by gbswales on 2007-08-07
Their doesnt seem to be a "guided repartition" option only one about using largest contigious space - Tried that but it says the hard disc is too small - 500gb with about half free
It goes through to the select partition size screen still - but with gobbledygook

this is what I am seeing file:///home/ubuntu/Desktop/Screenshot-Install.png


The manual option brought up some kind of partition manager which didnt seem to want to let me do anything.

---

### Post by Nike T on 2007-08-07
It says that it's too small because you don't have any unallocated space.  You haven't partitioned yet right?

---

### Post by gbswales on 2007-08-07
> **annda said:**
> are your options different than those?
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Yes they are - I am not getting the first option to resize the existing master partition:(

Is it something stupid like needing at least 50% free to resize partitions still - I remember that used to be the case years ago

---

### Post by gbswales on 2007-08-07
> **Nike T said:**
> It says that it's too small because you don't have any unallocated space.  You haven't partitioned yet right?

I thought the new installer was going to deal with all this for me - I have just a single partition, formatted NTFS on which windows resides - Its a 500gb disk and has about 240 gb free - I have a lot of data!

I just wanted something easy that would re-allocate some of that to the two partitions I will need for linux (why must it have two?).  

Whilst I have a 300gb drive as well that is mostly full with my data back ups

Thanks for all the input so far but it is beginning to look as if I will soon have to go back to windows and use somethething there to create some free space first - *sigh* - I thought Ubunto was being heralded as easier than windows!

---

### Post by Nike T on 2007-08-07
For the installer to work you have to have space that is free of partitions, not just free of data.  For that you could use gparted, a partitioning program

---

### Post by Paul133 on 2007-08-07
Isn't Gparted built into the installation? If you chose manual partitioning, you should be able to resize your Windows partition and then use the free space for Ubuntu. I know some people are worried about resizing NTFS partitions, but I've never had  a problem. If you don't want to bother with partitioning, you could consider "Wubi", which will allow you to install Ubuntu within Windows: [http://wubi-installer.org](http://wubi-installer.org). Good luck with Ubuntu!

---

### Post by CowzRule on 2007-08-07
This is how I installed from the LiveCD:
The first thing you need to do is resize your windows partition to free up the disk space you want for Ubuntu. On your top panel click System, Administration, GNOME Partition Editor to start Gparted. When you start it, it may mount your existing partitions. If it does it will put icons on the desktop and open file manager windows for them also. Just close the windows and right click the icons and select unmount.
In Gparted just select the partition you want to use and resize it. After resizing, reboot the machine back into the live cd. Restart gparted and select your new free space and make 3 partitions. One for /home, one for / and the last for swap. Swap size should be double your amount of memory. i.e. if you got 512 megs of memory, make your swap 1024 megs. For the size of /home and /, I go 60% for /home and 40% for /. Don't worry about formating the partitions as you'll get that option during install.
Once you got your partitions set up, double click the Install icon. After a bit you'll get to the part where it asks you what partitions to install to. Select manual. You'll then get a list of all of your available partitions. Just right click the partitions you just made and select edit. The dialog box will have a drop down list to select what you want the partition to be. If you get a warning box about the size being to small, just ignore it. I've gone through this a couple of times and I've never had any problems. Make sure you click the box to format those new partitions. There in the main partition listing. Once your done, click ok and continue.
I've listed this info from memory so I'm sure it's not exactly like what you'll see, but I'm sure you'll see what I'm talking about once you start do it.
Hope this help

---

### Post by gbswales on 2007-08-07
> **Paul133 said:**
> Isn't Gparted built into the installation? If you chose manual partitioning, you should be able to resize your Windows partition and then use the free space for Ubuntu. I know some people are worried about resizing NTFS partitions, but I've never had  a problem. If you don't want to bother with partitioning, you could consider "Wubi", which will allow you to install Ubuntu within Windows: [http://wubi-installer.org](http://wubi-installer.org). Good luck with Ubuntu!

THANK YOU :KS  This was the perfect solution - wubi worked just as it said with no intervention and I have my dual boot along with a neat virtual installation which got around the whole partitioning problem - I think this is an excellent solution for anyone who wants to seriously try Ubuntu without making too much of a committment or taking risks

thanks soo much

---

