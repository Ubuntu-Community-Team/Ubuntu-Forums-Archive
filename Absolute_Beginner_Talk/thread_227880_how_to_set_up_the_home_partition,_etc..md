---
title: "how to set up the /home partition, etc.?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-02
Hi everyone. I've been reading some instructions for installing Ubuntu, but none of them really get into the details of partitioning the HD the way I think I want to. In fact, some use the default Ubuntu method, which I don't think even creates a separate partition for sharing files between Windows and Ubuntu.

What I'd like is this:

1. Windows (NTFS)
2. Ubuntu(Ext3)
3. Shared space (FAT32)
4. /home (Ext3)
5. swap (created automatically?)

Now, I'm sure this comes from my ignorance of how Linux works, but what exactly makes the /home partition the /home partition? I mean, is there some special setup that occurs during installation or reformatting? Is it done once you are in Linux?

Before I begin this process, I want to make sure I know what to expect during the repartitioning, and right now I don't feel comfortable about setting up these four/five partitions.

If anyone can direct me to a guide that explains these things, I'd appreciate it. Also, maybe a quick explanation of how/when the /home partition is created would help too.

Thanks!
John

---

### Post by tuxinvader on 2006-08-02
During the install you will be asked if you want to manually partition or let Ubuntu do it for you. Select to do it manually and you will be taken to a nice gui that lets creatd and delete partitions. When creating a new partition you will be asked for size, filesystem type and mount point. It's all very straight forward and with your obvious grasp of partitioning you should have no problem. IMHO it's easier in Ubuntu than it is in Winblows

---

### Post by aysiu on 2006-08-02
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by JohnJSal on 2006-08-02
Thanks. I think I can see how it might be fairly easy with most of the partitions, but I'm still unclear if anything special needs to be done to create the /home partition. Do I have to name it this during partition time? Does it need to be a particular size? Is there anything magical about this partition, or does it only become the '/home' partition after you get into Ubuntu and start doing things?

---

### Post by [S|G] on 2006-08-02
On Linux, unlike windows, you don't have drive letters and instead choose which partition will be mounted under a certain directory. By default everything would be placed in the same partition as your root (/).

Partitions are areas on your hard drive that hold data indepently. This means that if you have to format/delete one partition, the other one is left intact. It is somewhat as if you had more than one hard drive.

The partitioning process is allocating free space in your disk and telling who is going to use what. So it would work like this: you assign some free space to your root partition, but not all the free space available. Then you assign some more free space for another partition, format it as EXT3 and then you tell linux to mount it on your /home directory.

You could actually mount it anywhere you wanted to, but mounting it as /home means that your personal files will be safe in case you decide to reinstall linux, format it or whatever, since all user files are stored in /home/UserName. (Any directory under /home will be using the partition that you mounted for home).

You can mount another partition under your /home, so you can create things like / (root, partition A), /home (partition B), /home/YourUser (still using partition B), /home/windows (partition C). You can see where things are being mounted by looking at your /etc/fstab.

You can create a partition anytime you like, but ideally you should do it while installing the system to avoid having to move files around and changing mountpoints.

Hope it helps a bit

---

### Post by [S|G] on 2006-08-02
> **JohnJSal said:**
> Thanks. I think I can see how it might be fairly easy with most of the partitions, but I'm still unclear if anything special needs to be done to create the /home partition. Do I have to name it this during partition time? Does it need to be a particular size? Is there anything magical about this partition, or does it only become the '/home' partition after you get into Ubuntu and start doing things?

For desktop systems usually you allocate most free space for your /home so you can save your files. The root partition doesn't need much more than 5gb of space, so you can assign the remaining space to your /home.

---

### Post by wpshooter on 2006-08-02
> **'[S|G] said:**
> For desktop systems usually you allocate most free space for your /home so you can save your files. The root partition doesn't need much more than 5gb of space, so you can assign the remaining space to your /home.

Personally, I like to allocate more than 5gb (or the 2 to 3gb recommended by Ubuntu) for the /root partition.  

If you have say for instance an 80gb drive (that was to be used strictly as a Ubuntu machine), I would do /root partition 20gb, /home partition 58gb & swap partition 1 or 2gb.

Good luck.

---

### Post by JohnJSal on 2006-08-02
The /home partition needs to be that big? I figured it would simply be a small section where preferences and options are stored. Is it also used for storing files? I thought that might happen on the main Ubuntu partition instead.

---

### Post by aysiu on 2006-08-02
The /home partition is a lot like C:\Documents and Settings in Windows.

It holds all the user information *and* the user files.

---

### Post by JohnJSal on 2006-08-02
But when I install any programs, etc. do those go in the / folder or the /home folder?

---

### Post by [S|G] on 2006-08-02
When you install programs they usually go to /usr (which is on the same partition as your /). But usually programs don't take a lot of space - user files do. Every document you save, musics you have on your computer, things you download, etc, will go to your /home directory.

---

### Post by aysiu on 2006-08-02
Just to give you a general idea--with Xubuntu, Kubuntu, and Ubuntu installed... *and* all my extra programs, my Ubuntu installation is 3.5 GB total.

My entire music collection is 40 GB.

---

### Post by JohnJSal on 2006-08-02
> **'[S|G] said:**
> When you install programs they usually go to /usr (which is on the same partition as your /). But usually programs don't take a lot of space - user files do. Every document you save, musics you have on your computer, things you download, etc, will go to your /home directory.

But shouldn't a lot of those things go into the shared partition instead?

---

### Post by aysiu on 2006-08-02
> **JohnJSal said:**
> But shouldn't a lot of those things go into the shared partition instead?
Ah, good point. What I've done on my computer is have a Ubuntu partition, a documents partition, and a Windows partition. I don't have a separate /home, as my settings don't really matter to me that much when I reinstall the new version of Ubuntu.

---

### Post by JohnJSal on 2006-08-02
Ok, an additional question: instead of creating a separate partition for /home, is it just possible to backup this directory when you want to reinstall Ubuntu, and then replace the new one with the backedup one after the fresh install?

Also, does the automatic partition on the Dapper disc allow you to create a shared space partition, or must you do it manually even for this?

Thanks.

---

### Post by mostwanted on 2006-08-02
> **JohnJSal said:**
> But when I install any programs, etc. do those go in the / folder or the /home folder?

The program settings go into home, the program itself is scattered along the rest of / (/home is a sub folder to /, so your question was technically an oxymoron :p).

---

### Post by aysiu on 2006-08-02
> **JohnJSal said:**
> Ok, an additional question: instead of creating a separate partition for /home, is it just possible to backup this directory when you want to reinstall Ubuntu, and then replace the new one with the backedup one after the fresh install? The whole point of creating a separate /home partition is so that you don't have to do that. Your settings will remain intact, even when you reinstall.

---

### Post by JohnJSal on 2006-08-02
> **aysiu said:**
> The whole point of creating a separate /home partition is so that you don't have to do that. Your settings will remain intact, even when you reinstall.

But it is still possible, right? It seems easier to do this so you don't have to worry about making your /home partition too large or too small.

But also, what if you have settings, etc. in /home and then you reformat the root partition. How do you then remove all the settings in /home that belonged to programs you no longer have installed in Ubuntu after the reformat/reinstall? Do you have to delete them manually? Or does the uninstall manager still detect them, even if the program itself isn't there anymore?

---

### Post by aysiu on 2006-08-02
Unless your hard drive is 10 GB, I don't think you have to worry about your /home partition being too large or too small, especially if you're storing your documents on their own separate partition to share between Windows and Ubuntu. Configuration files tend to take up very little space.

And you don't need to remove settings for programs that are no longer installed. You can if you want, but they don't take up much room. And if you reinstall those programs again later, you can have your old settings still.

---

### Post by JohnJSal on 2006-08-02
> **aysiu said:**
> Unless your hard drive is 10 GB

Well, it's not quite that small, but space is an issue to a certain degree. My HD is 60GB, and by the time I install Ubuntu I plan to have 30GB free. A lot of that other 30GB is music, so I don't know how I would go about moving that into the shared partition.

But here's where I'm confused some more. After the repartitioning, does this mean I can't put anymore files into the NTFS partition, since Ubuntu will take up all the rest of the free space with the other partitions? What if I need to put more music, or install a game?

I guess my plan is this: I want to use Ubuntu just to play around with Linux. I still plan to use Windows to do audio/video stuff, so I'm thinking that my shared space partition doesn't even need to be more than 1-2GB, just big enough to put a few files here and there in case I need to share them. I think I will still keep my NTFS partition around 40-45 GB of the 60, and Ubuntu will take up the rest, with a small space for sharing files.

Is that a decent plan, or is it something I might regret?

---

### Post by JohnJSal on 2006-08-02
> **aysiu said:**
> Unless your hard drive is 10 GB

Well, it's not quite that small, but space is an issue to a certain degree. My HD is 60GB, and by the time I install Ubuntu I plan to have 30GB free. A lot of that other 30GB is music, so I don't know how I would go about moving that into the shared partition.

But here's where I'm confused some more. After the repartitioning, does this mean I can't put anymore files into the NTFS partition, since Ubuntu will take up all the rest of the free space with the other partitions? What if I need to put more music, or install a game?

I guess my plan is this: I want to use Ubuntu just to play around with Linux. I still plan to use Windows to do audio/video/games, etc., so I'm thinking that my shared space partition doesn't even need to be more than 1-2GB, just big enough to put a few files here and there in case I need to share them. I think I will still keep my NTFS partition around 40-45 GB of the 60, and Ubuntu will take up the rest, with a small space for sharing files.

Is that a decent plan, or is it something I might regret?

---

### Post by aysiu on 2006-08-02
If I had 60 GB, this is what I'd do:

15 GB for Windows (NTFS)
44 GB for documents (Ext3 or FAT32)
512 MB for /home (Ext3)
512 MB for swap

---

### Post by JohnJSal on 2006-08-02
> **aysiu said:**
> If I had 60 GB, this is what I'd do:

15 GB for Windows (NTFS)
44 GB for documents (Ext3 or FAT32)
512 MB for /home (Ext3)
512 MB for swap

So the 44GB would be the root install? I'd like to install Ubuntu on Ext3 (that seems to be normal), but that would mean having another partition for shared files that Windows could read/write.

Also, I have 1GB RAM, so should I make the swap 2GB?

(So much to consider!) :)

---

### Post by aysiu on 2006-08-02
Shoot! I forgot about root.

How about this?

15 GB for Windows (NTFS)
39 GB for documents (Ext3 or FAT32)
5 GB for / (Ext3)
512 MB for /home (Ext3)
512 MB for swap

---

### Post by JohnJSal on 2006-08-02
> **aysiu said:**
> Shoot! I forgot about root.

How about this?

15 GB for Windows (NTFS)
39 GB for documents (Ext3 or FAT32)
5 GB for / (Ext3)
512 MB for /home (Ext3)
512 MB for swap

That's not bad. My only concern is that having any new programs I install on a FAT32 drive instead of NTFS might hurt performance, such as for games, etc. Is there much of a difference between NTFS and FAT32 that this would be an issue?

Also, 15GB for Windows would be impossible at this point, because about 10GB of my HD are music. How do I get that music into the shared partition and off the NTFS partition, so it can shrink?

---

### Post by aysiu on 2006-08-02
The programs would be installed on either the NTFS or / partition, not the FAT32 one. As for shrinking and moving... that's where external media comes in handy (external hard drive, iPod, CDs, DVDs...)

---

### Post by JohnJSal on 2006-08-02
> **aysiu said:**
> The programs would be installed on either the NTFS or / partition, not the FAT32 one. As for shrinking and moving... that's where external media comes in handy (external hard drive, iPod, CDs, DVDs...)

But if the Windows (NTFS) partition is shrunk to 15GB, how would anything get installed to that partition later? It seems like I'd have no choice but to put it on the FAT32 partition, since that will be the one with the space.

---

### Post by aysiu on 2006-08-02
With no documents or files--just programs--your Windows partition would need to be larger than 15 GB?

Hm. That does pose a problem.

How about this, then?

25 GB Windows NTFS
27 GB documents (Ext3 or FAT32)
7.5 GB / Ext3
512 MB Swap

I would advise making documents Ext3 and then installing [http://www.fs-driver.org](http://www.fs-driver.org) on Windows to read/write it. Then, for the important settings (Firefox and Thunderbird for me), put those on the documents partition and then symlink them to the /home folder of the / partition.

---

### Post by JohnJSal on 2006-08-02
> **aysiu said:**
> With no documents or files--just programs--your Windows partition would need to be larger than 15 GB?

Well, just Windows itself is probably about 15GB, but I'm talking about installing games, or other programs that I want to use just under Windows. I know I can install these into the share partition, but I'm worried that their performance might be affected by the different format type (FAT32). So I was thinking of keeping the NTFS partition around 40GB or so to give me the space to keep files/programs there and not on the share partition.

---

### Post by aysiu on 2006-08-02
Seriously? My Windows XP uses about 7 GB with all the programs I have installed. I don't play games, but the operating system itself shouldn't take up 15 GB. Well, look at my revised proposed plan. Is 25 GB enough?

---

### Post by JohnJSal on 2006-08-02
> **aysiu said:**
> Seriously? My Windows XP uses about 7 GB with all the programs I have installed. I don't play games, but the operating system itself shouldn't take up 15 GB. Well, look at my revised proposed plan. Is 25 GB enough?

Well, maybe I misspoke before. My current Windows installation is around 15GB (without music), but that does include everything else on my HD, so it's not really just Windows. I have some games, Dreamweaver, etc. etc. The reason I'm still considering all these things as part of the Windows partition is because I don't know how to (or if I even should) move all of this stuff to the shared partition. There's no reason to, since I won't be using these things in Ubuntu, and some things (Firefox, Thunderbird, etc.) have different versions of Win and Linux anyway, while other things (games) can't be played on Linux. So it seems pointless to move this stuff, and the prospect of uninstalling it all and reinstalling it in the new partition (if that's how it's done) is not enticing. So I figure even after all my cleanup, my Windows partition will be around 15GB, because that includes some games and programs that I don't want to move.

---

### Post by jimbren on 2006-08-02
most things you install will go into /bin or /opt, but all of your documents will go into /home/youruser.  Also, your downloads and stuff like that will go there by default.

---

### Post by stormblue on 2006-08-02
Although Thunderbird and firefox have different versions between linux and windows, they can share a profile.  That means all your e-mails and bookmarks would be available in both thunderbird and firefox.  Also, if you use GAIM you can share a profile for that too.  This is really nice on a dual boot machine.  This is just something to consider.  The profiles aren't that big so it's not a consideration of space, but just make sure both OS's can read them.  Someone else can help you getting it to work in windows if you choose the ext3 parition over the fat32, sorry, I don't know much about it.

---

### Post by JohnJSal on 2006-08-02
> **stormblue said:**
> Although Thunderbird and firefox have different versions between linux and windows, they can share a profile.  That means all your e-mails and bookmarks would be available in both thunderbird and firefox.  Also, if you use GAIM you can share a profile for that too.

So how does this sharing of profiles work? Let's say I already have FF installed on my HD right now (which is NTFS and a single partition). I then repartition to put on Ubuntu, and of course Ubuntu comes with FF already. What step do I take to make sure they share the profile? On the Windows partition, the profile folder will be in one place and that's where FF will look for it. On Ubuntu it will be elsewhere and that's where that version of FF will look. So how do I make FF look for the profile in a single, shared place?

---

### Post by aysiu on 2006-08-02
Try [this](http://www.ubuntuforums.org/showthread.php?t=203524).

---

### Post by JohnJSal on 2006-08-02
Excellent! Thanks! Slowly things are starting to come together in my head. :)

---

### Post by aysiu on 2006-08-02
> **JohnJSal said:**
> Excellent! Thanks! Slowly things are starting to come together in my head. :)
Slow is good. If there's anything that makes me wince on these forums--it's people rushing into things. Planning is good.

---

### Post by stormblue on 2006-08-02
Check out the [HOWTO: Share Thunderbird and Firefox]("http://http://www.ubuntuforums.org/showthread.php?t=203524")

You need to be able to read/write to the profile from both linux and windows and NTFS doesn't support this.  You might be able copy the profile over to linux using ext3 or ext2 and use that from windows with the right software installed on windows (Search on the forum).  The easiest way is to use a Fat32 partition.  I'm sorry I can't help you beyond this.  I've never done it with anything other than the Fat32 partition.  Although, I can tell you that NTFS won't work.

---

### Post by bbzbryce on 2006-08-02
> **aysiu said:**
> Seriously? My Windows XP uses about 7 GB with all the programs I have installed. I don't play games, but the operating system itself shouldn't take up 15 GB. Well, look at my revised proposed plan. Is 25 GB enough?

Windows Vista will require 15GB of space to install.  With harddrives being quite cheap these days (I bought a 30GB hard drive around 98 for $300 whereas I just bought a 150GB Raptor for $200 and I know some places you can get hard drives for as cheap as 3GB/$).  Anyways my partition structure:

30GB Windows XP (/media/XP - NTFS)
30GB Windows Vista (/media/Vista - NTFS)
30GB Ubuntu (/ - EXT3)
~56GB Ubuntu (/home - EXT3)
4GB Swap


> **JohnJSal said:**
> So how does this sharing of profiles work? Let's say I already have FF installed on my HD right now (which is NTFS and a single partition). I then repartition to put on Ubuntu, and of course Ubuntu comes with FF already. What step do I take to make sure they share the profile? On the Windows partition, the profile folder will be in one place and that's where FF will look for it. On Ubuntu it will be elsewhere and that's where that version of FF will look. So how do I make FF look for the profile in a single, shared place?

I personally use [Google Browser Sync]("http://www.google.com/tools/firefox/browsersync/") for these purposes.  Starting and closing firefox takes a bit longer because it has to get/put updates but makes the whole process very simple.

As for sharing a profile in Thunderbird its almost more of a pain than anything.  I did it for awhile but I had problems with folders being marked as not read even though the permissions were perfect.  My solution to this problem was thunderbird in Ubuntu and using the gmail interface in windows.  I'm not in windows very often so this was a good solution.

---

### Post by aysiu on 2006-08-02
4 GB of swap...?

---

### Post by stoft on 2006-08-02
Not sure if it will help but here's my current setup, an ubuntu/winXP system on a 60GB drive.

```

The partitions:

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1573    12635091    7  HPFS/NTFS
/dev/hda2            1574        7295    45961965    f  W95 Ext'd (LBA)
/dev/hda5   *        1574        2356     6289416   83  Linux
/dev/hda6            2357        2487     1052226   83  Linux
/dev/hda7            2488        2552      522081   82  Linux swap
/dev/hda8            2553        7295    38098116    c  W95 FAT32 (LBA)

Partition size in human-readable form:

Filesystem	Size	Used	Avail	Use%	Mounted on
/dev/hda1	13G	11G	1,2G	91%	/media/hda1
/dev/hda5	6,0G	3,5G	2,2G	62%	/
/dev/hda6	963M	720M	193M	79%	/home
/dev/hda8	37G	36G	1,1G	97%	/media/hda8

```

First off I'd play around with a live-CD if you haven't already. Then, if you still want to, I'd install Ubuntu on a 6-7GB partition (including /home) and try to move out as much as possible from C: to the share partition. That should give you space to play around a bit so that next time you do an install from scratch you'll know what you want.

---

### Post by stormblue on 2006-08-02
> **bbzbryce said:**
> 

30GB Windows XP (/media/XP - NTFS)
30GB Windows Vista (/media/Vista - NTFS)
30GB Ubuntu (/ - EXT3)
~56GB Ubuntu (/home - EXT3)
4GB Swap


4GB seems incredible excessive.  I have a gig of ram and 2gb swap and I don't think I've ever seen my swap being used.  I'm currently using just under 300megs of ram for firefox, thunderbird, GAIM, Bluefish, terminal, package manager, system monitor, and Gnome.  I've heard that double your ram is a good idea, but anything more than 1 gig, with rare exception, doesn't make sense.



> 

As for sharing a profile in Thunderbird its almost more of a pain than anything.  I did it for awhile but I had problems with folders being marked as not read even though the permissions were perfect.  My solution to this problem was thunderbird in Ubuntu and using the gmail interface in windows.  I'm not in windows very often so this was a good solution.

If you do plan on dual booting sharing the profiles is the way to go.  I can attest to having no problems, so it can work correctly and once set up works like a charm.  Although, the other solution would work as well if you aren't dual booting that often.

---

### Post by JohnJSal on 2006-08-02
> **stoft said:**
> 
Partition size in human-readable form:

Filesystem	Size	Used	Avail	Use%	Mounted on
/dev/hda1	13G	11G	1,2G	91%	/media/hda1
/dev/hda5	6,0G	3,5G	2,2G	62%	/
/dev/hda6	963M	720M	193M	79%	/home
/dev/hda8	37G	36G	1,1G	97%	/media/hda8
[/CODE]

Is it necessary for me to understand what the /dev/hda terms mean during the partition phase of installation? I don't know what the difference is between them, except that they stand for different partitions. But if I need to manually choose them when mounting, I'll have to do more investigating, because right now I have no clue what it means or why they are numbered the way they are.

---

### Post by cantormath on 2006-08-02
you could do a separate partition for windows.....and install ubuntu.......normal dual boot.....and use ntfs-3g to access the windows partition from linux read/write.

_tutorial:_
[http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/](http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/)

---

### Post by stormblue on 2006-08-02
> **JohnJSal said:**
> Is it necessary for me to understand what the /dev/hda terms mean during the partition phase of installation? I don't know what the difference is between them, except that they stand for different partitions. But if I need to manually choose them when mounting, I'll have to do more investigating, because right now I have no clue what it means or why they are numbered the way they are.

It isn't necessary to know the difference.  Once you see the  partition tool it's more user friendly than a windows XP install.  All you need to be able to do is pick out which is you swap, FAT32, etc, etc, etc or whatever you decide to go with. 


I'll see if I can find a screen shot so you can see what I mean.

---

### Post by JohnJSal on 2006-08-02
> **stormblue said:**
> It isn't necessary to know the difference.  Once you see the  partition tool it's more user friendly than a windows XP install.  All you need to be able to do is pick out which is you swap, FAT32, etc, etc, etc or whatever you decide to go with. 


I'll see if I can find a screen shot so you can see what I mean.

Thanks. These are the screenshots that really helped me:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

But I wasn't sure if I'd actually have to choose those hda options myself, because in one screen you can see them under the list of partitions. But I guess it's just a matter of knowing which is which based on how you are sizing them, except that Windows will be hda1, right?

---

### Post by bbzbryce on 2006-08-02
> **aysiu said:**
> 4 GB of swap...?

Yeah 4GB isn't really necessary but I have more than enough to spare.  I also have a 250GB drive for my music and whatnot.  I read somewhere that your swap space should be about double your ram and since I have 2GB I just plugged in that 4GB number.

In all actuallity it appears my used swap never goes above 83MB so 4GB is quite a bit but no need to change it.  Like I said before hard drives are pretty cheap.

---

### Post by JohnJSal on 2006-08-02
> **bbzbryce said:**
> Yeah 4GB isn't really necessary but I have more than enough to spare.  I also have a 250GB drive for my music and whatnot.  I read somewhere that your swap space should be about double your ram and since I have 2GB I just plugged in that 4GB number.

In all actuallity it appears my used swap never goes above 83MB so 4GB is quite a bit but no need to change it.  Like I said before hard drives are pretty cheap.

So if I have 1GB RAM, I don't really need to do 2GB for swap? Should I even do 1GB?

---

### Post by stormblue on 2006-08-02
I'd say 1gb isn't excessive, but you could probably go with 512 if you need the space.  How much ram do you have in your system.  The more ram you have the less important it is on the desktop.

---

### Post by JohnJSal on 2006-08-02
> **stormblue said:**
> I'd say 1gb isn't excessive, but you could probably go with 512 if you need the space.  How much ram do you have in your system.  The more ram you have the less important it is on the desktop.

I have 1GB RAM, and it's a laptop, in case that matters.

---

### Post by stormblue on 2006-08-02
I have 1gb too and I've never used my swap.  You might want to do 1gb, but if you need the space you could go with 512 or 256.  My firefox sometimes goes crazy and takes up 100megs of memory, but other than that...1gb should be fine.

---

### Post by bbzbryce on 2006-08-02
> **JohnJSal said:**
> So if I have 1GB RAM, I don't really need to do 2GB for swap? Should I even do 1GB?

It's up to you really and the applications you use.  I just found an [article]("http://www.sunmanagers.org/pipermail/summaries/2005-February/006111.html") confirming just that and that the 2 x memory is no longer a recommendation. Although they say that too much can be a bad thing I think it's better to go with a safe number and see what you end up using on a regular full load basis.  Obviously next time I partition I'll probably knock mine down to 1GB.

---

### Post by stoft on 2006-08-02
> **JohnJSal said:**
> I have 1GB RAM, and it's a laptop, in case that matters.

In some cases suspend-to-disk (a.k.a. "hibernate" if I'm not mistaken) writes to /swap. If /swap isn't at least as large as your RAM suspend-to-disk won't be able to write all of your RAM to /swap and hibernate will not work. Seeing as you're on a laptop I'm guessing you'll want to be able to have suspend and suspend-to-disk functionality. In other words, make /swap as big as your RAM and maybe just a tad bit more to be on the safe side.

---

### Post by JohnJSal on 2006-08-02
> **stoft said:**
> In some cases suspend-to-disk (a.k.a. "hibernate" if I'm not mistaken) writes to /swap. If /swap isn't at least as large as your RAM suspend-to-disk won't be able to write all of your RAM to /swap and hibernate will not work. Seeing as you're on a laptop I'm guessing you'll want to be able to have suspend and suspend-to-disk functionality. In other words, make /swap as big as your RAM and maybe just a tad bit more to be on the safe side.

Interesting point. But does suspend always need the full amount, or are you just saying that it's *possible* it may need the full amount some times?

---

### Post by stoft on 2006-08-03
> **JohnJSal said:**
> Interesting point. But does suspend always need the full amount, or are you just saying that it's *possible* it may need the full amount some times?

My shooting-from-the-hip guess is that suspend, when writing to disk, will write all of the RAM to disk. There seem to be at least two different suspend solutions available (from [wikipedia]("http://en.wikipedia.org/wiki/Hibernate_(OS_feature)")):
> In the Linux kernel, Hibernate or suspend-to-disk is implemented by swsusp which is inbuilt into the 2.6 series. An alternative implementation is Suspend2 which is available as patches for the 2.4 and 2.6 kernels. It provides advantages such as support for SMP, 4GB high mem and preemption. Currently work is being done on merging Suspend2 into the mainline kernel.
At least suspend2 has the possibility to either write to swap or a file. Things I don't know are:
1) Which is the standard ubuntu-solution?
2) Does the out-of-the-box solution write to /swap or a file under e.g. /tmp?
3) If the default solution writes to /swap, how easy is it to change it if you don't want to use /swap?

and lastly:
4)Is not using /swap that much better?

To the last question I don't think there's a simple answer now that RAM is so abundant, and maybe even a potential [holy war]("http://catb.org/jargon/html/H/holy-wars.html") lurking. My recommendation is either do some good research as to the ubuntu-solution and how it works, or create a /swap space big enough to cover your back.

---

