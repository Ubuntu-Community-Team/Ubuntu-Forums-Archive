---
title: "Changing Partitions"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Duffanator on 2007-02-16
During the install of Ubuntu, when it let you chose how much space it would use, I thought whatever I chose would be how much of my harddrive Ubuntu would get. However, upon logging onto Windows I find that it has only 1.98gb of free space. This is NOT what I wanted.

I only wanted Ubuntu to use about 10gb in total of my 40gb harddrive.

Even after this I thought, hey, maybe I wont need to use Windows anymore.

Turns out I do. I cant figure out how to install any games, I don't really want to spend hours doing it and I would prefer if Windows had ALOT more free space.

Sure, I could download WINE (even though I can't even get that to work) but looking at some website about it some of the games I want to play arn't even mentioned, or don't have full functionality through WINE.

If the easiest thing to do is completely remove Ubuntu (and reinstall it on a smaller partition) how do I do that?

What do I use to format whatever space Linux is using and give it back to Windows as free space?

---

### Post by kanha on 2007-02-16
log into ubuntu
open accessories-->terminal
type gparted
reduce the size of ubuntu drive to 10 gb


again log back in windows
open control panel ---> computer management ----> disk management
extend windows partition to fill all free space

---

### Post by bodhi.zazen on 2007-02-16
kanha's basic idea is what you need to do, however you will need to do it a little differently.

First, how much free space did/do you have on the hard drive ?

You can likely squeeze Ubuntu into as little as 5 Gb if needed.

First, you can not manage partitions as mounted. This means you will need to boot to a live CD.

The Ubuntu cd will do the job, but you may want to download teh gparted CD :

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)


OK -

Now you can not add free space to a partition unless it follows the partition.

Once you resize, or reduce the Ubutnu partiton you will likely have :

Windows
Ubuntu
free space
swap

Or 

Windows
swap
Ubuntu
Free space

You will first need to move the partitions so you have 

Windows
Free space
Ubutnu
swap

Then add the free space to windows.

===========================

In fact the easiest thing to do is likely

Boot the Ubuntu live CD

Delete all the Ubuntu partitions

resize your windows partiton to the correct size

re-install Ubuntu

---

### Post by Wikzo on 2007-02-16
I want to ask about almost the same thing:

I got Windows XP and Ubuntu as well, but I haven't so much space on the Linux partition. Can I just resize it (make it a little bit bigger) in the live cd with Gparted? It won't do anything to Ubuntu/Windows if I just make the Ubuntu a bit bigger and the Windows a bit smaller?

---

### Post by bodhi.zazen on 2007-02-16
> **Wikzo said:**
> I want to ask about almost the same thing:

I got Windows XP and Ubuntu as well, but I haven't so much space on the Linux partition. Can I just resize it (make it a little bit bigger) in the live cd with Gparted? It won't do anything to Ubuntu/Windows if I just make the Ubuntu a bit bigger and the Windows a bit smaller?

You should have no problem.

However see my comments about allocating the free space. For example after resizing windows you will have:

Windows
free space
Ubuntu

And you will thus not be able to add the free space to ubuntu unless you move the partition to be 

Windows
Ubuntu
free space

Then you can add the free space to ubuntu :p

---

### Post by neotasic1 on 2007-05-03
This is an interesting thread.  I too have a dual boot machine with XP and Ubuntu 7.04 but the Linux installation resides entirely on its own 200GB hard drive.  The entire drive is formatted ext3 with separate partition for swap.  After reading the ubuntu documentation at [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) it has become apparent to me that I probably would have been better off creating a separate partition for my /home directory.  My question is can I use the gparted on the installation cd to create a separate partition on this drive to install my home directory on, and can I then transfer my home directory and all its contents to this newly created partition without losing all my settings and data?

**All done and working perfectly - another great success story for the Ubuntu community - Thanks all.**

---

### Post by bodhi.zazen on 2007-05-03
> **neotasic1 said:**
> This is an interesting thread.  I too have a dual boot machine with XP and Ubuntu 7.04 but the Linux installation resides entirely on its own 200GB hard drive.  The entire drive is formatted ext3 with separate partition for swap.  After reading the ubuntu documentation at [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) it has become apparent to me that I probably would have been better off creating a separate partition for my /home directory.  My question is can I use the gparted on the installation cd to create a separate partition on this drive to install my home directory on, and can I then transfer my home directory and all its contents to this newly created partition without losing all my settings and data?

Yes, very easily

But you must resize your ubuntu partition from a live CD, either Ubuntu or gparted.

IMO gparted is worth the download ...

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-6.iso)

Once that is done, move home :

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by indytim on 2007-05-03
Neotastic1,

When you're re-sizing according to Bodhi.zazen's recommendations, you may want to consider carving up your 200G hd into additional partitions.  With additional partition(s) to house some of your data, it will live through future upgrades of your Lx operating system.  For example, I have a dedicated 320G hd that contains all of my backup data, media files, financial data etc.  It is independent of the hd where my ops are stored.  A case of somewhat extreme's, but it works.

IndyTim

---

### Post by neotasic1 on 2007-05-03
Thank you for that - i have downloaded the gparted livecd iso and burned it to disk.  I will download the documentation also (good suggestion) and get it all done today.  Many thanks for quick response.

---

### Post by neotasic1 on 2007-05-03
> **indytim said:**
> Neotastic1,

When you're re-sizing according to Bodhi.zazen's recommendations, you may want to consider carving up your 200G hd into additional partitions.  With additional partition(s) to house some of your data, it will live through future upgrades of your Lx operating system.  For example, I have a dedicated 320G hd that contains all of my backup data, media files, financial data etc.  It is independent of the hd where my ops are stored.  A case of somewhat extreme's, but it works.

IndyTim
Sounds like a good suggestion.  I also have a number of hard drives both IDE and SATA along with a IDE RAID array so i could create a number of partitions on different drives for redundancy and failsafe.  It does raise the question though.  I was under the impression, that if i kept my /home directory on a separate partition (on or off the same physical hard drive) it would allow me to upgrade to future distributions without losing my settings and data files (which I thought were stored by default in the /home directory.)  Is this not the case?

---

