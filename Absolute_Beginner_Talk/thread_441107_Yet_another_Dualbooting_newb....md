---
title: "Yet another Dualbooting newb..."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by AlfAlf on 2007-05-12
Hi everyone,

I'm looking into dualbooting XP Pro and Ubuntu 6.06, but I'm not too sure about what filesystems to use, nor if my proposed layout will be workable or practical.

I have two Hard Drives, and was thinking of partitioning them like this:

1. 80GB System drive

* 30GB NTFS for XP
* 30GB Ext3 for Linux (including boot & swap partitions, but I'm unsure about size & type for those)
* 20GB FAT32 /home & personal folders etc (needs to be easily accessible from windows too)


2. 200GB Media drive

* 200GB NTFS


Assuming it's worth it, I'd like both Operating systems to be accessible via the other to (hopefully) avoid having to do a reinstall to rectify any problems that will inevitably occur - but would it be possible to do so with this setup?
As far as I know, you can mount Ext3 partitions in XP without too much trouble, but what's the state of play with Ubuntu regarding NTFS read & write - does this vary between releases? Would it be more trouble than it's worth putting my /home folder on the NTFS media drive? Is Ext3 even the best option for the Linux partition?

Sorry for so many questions, but I really don't want to screw this all up! :)

---

### Post by Happy_Man on 2007-05-12
This is a wonderful setup...nice job!

Ubuntu can happily read/write to NTFS using a fun little app called ntfs-3g. I think it's available in the repos now, so all you have to do is open up a terminal (System --> Accessories --> Terminal) and type:
```
sudo apt-get install ntfs-3g ntfs-config
```

If you want your /home on the external, I would suggest just reformatting it as ext3, it will save much hassling later. ext3 is _absolutely_ the best choice for Linux partition, don't worry about that. Hope you have a smooth ride!

---

### Post by starcraft.man on 2007-05-12
As for how much space each of the linux partitions needs... I'd say yours should look like this, root and home should be ext3.

Win XP 30 GB
Root (/) 8 GB
Swap-file 2 GB
home (/home) 20 GB
Share fat32 20 GB

I am not exactly sure why you want to format your media drive to NTFS, but you can if you want to (I just made my whole usb external fat32, I don't have files bigger than 4 GB) you will just have to remember to install the ntfs-3g drivers.

In response to your questions, yes its easy to set up a dual boot, long as you have XP installed first Ubuntu will load your grub so you can boot both. You can also mount and write to ext3 in XP, you need the drivers though I forget their name... No the read write of NTFS doesn't vary from release, just depends on the ntfs-3g drivers. I don't know why you would want to put your home folder on your NTFS partition you can but eh... I don't see any real reason to. Ext3 is stable and capable as a file system, use it.

Have fun, you may consider merging your share/home in my suggestion into one and then just mounting your home into XP. And I don't think i'd recommend NTFS for your external/media storage, I suggest fat32 or better yet like happy said ext3, you may not log into windows much soon :p

Have fun :)

Oh and just one question, why are you using 6.06 rather than Feisty? Unless your a business or have some other need for the long term support, there usually isn't a reason to use Dapper for the average user.

---

### Post by Pistolla on 2007-05-12
I couldn't agree more with Happy man:guitar: 
Happy man your quote on yer sig is from Ghandi and yes we must be the guy/gal :lolflag:

---

### Post by AlfAlf on 2007-05-12
Thanks for the quick replies guys!

I would use FAT32 for the Media Drive since I don't tend to have files over 4GB and both OS's could access it straight away without any configuring, but I'd like to have the option to exceed that limit just in case I decide to backup my PS2 games etc.

Does anyone here have experience of using ext3 drives in XP - do you actually have to mount the drive at each startup, or can you access it as per usual once the drivers are installed?
Lets say I did keep the drive as NTFS, would I have to activate NTFS-3G every time I boot into ubuntu, or is it just a case of telling the app the drive is there during the initial config and that's it? I'd just like to avoid as much messing about as I can (though that'll probably pale in comparison to when I start backing everything up this evening) :)

---

### Post by starcraft.man on 2007-05-12
> **AlfAlf said:**
> Thanks for the quick replies guys!

I would use FAT32 for the Media Drive since I don't tend to have files over 4GB and both OS's could access it straight away without any configuring, but I'd like to have the option to exceed that limit just in case I decide to backup my PS2 games etc.

Does anyone here have experience of using ext3 drives in XP - do you actually have to mount the drive at each startup, or can you access it as per usual once the drivers are installed?
Lets say I did keep the drive as NTFS, would I have to activate NTFS-3G every time I boot into ubuntu, or is it just a case of telling the app the drive is there during the initial config and that's it?

Just a note for the record, a lot of PS2 games aren't actually DVDs, a good many are just CDs... and you can always use an archiving utility to span files over the 4 GB mark. Not to mention your home partition (20-40 GB depending) will be able to exceed the limit until you archive them for storage onto your media hard drive. 

And your looking for [this...]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_read_Linux_partitions_.28ext2.2C_ext3.29_in_Windows_machine") 
Doesn't matter its in feisty wiki, it applies to all versions I think. I haven't done it myself though >.>.

And no, you don't have to reactivate the ntfs-3g config, long as you do it correctly and mount it, it should stay that way unless you decide to unmount >.>.

Theres more documentation on mounting a windows partition as read write in ubuntu guide, just go back to dapper or whchever version you install with.

---

### Post by undertakingyou on 2007-05-12
Here is a link for EXT support in windows. [http://www.fs-driver.org/](http://www.fs-driver.org/)  One thing that I have noticed though is that on occasion, windows will look at that partition and say that it is RAW unformatted space.  Whenever that happens I find a restart to do the trick. It is anoying though.  That asside, I do agree, use EXT3 for your "home drive"  It will play nicer, and is more secure than fat32.

---

### Post by AlfAlf on 2007-05-12
Thanks for that ext3 driver link, undertakingyou, that looks better than the other ones I've come across. But when you say "home drive", do you mean the /home partition or the drive for Linux itself? I don't use the My Documents folder in windows, but use a personal folder on the C:\ drive (gives easier command line access, among other things).
I'd like to have this folder and /home in the same partition - seeing as I use this personal folder in windows all the time, maybe FAT32 would be better for that particular partition since windows recognises it without any problems, even though the higher probability of file integrity being compromised than with ext3 does bother me quite a bit.

> ..you don't have to reactivate the ntfs-3g config, long as you do it correctly and mount it, it should stay that way unless you decide to unmount

That's really good news actually, as I wouldn't have enough space at the moment to shuffle everything about during reformatting. So I'll keep it as NTFS for now, I can always move it over if I drop Windows completely, by then I'll probably have a larger SATA drive when I eventually get a new mobo.


Right, just got a couple more questions regarding the more "essential" partitions, then I think I'll be ready to make a start...

**Boot** - Will this be created during the install, or will I need to allocate space for it when I slice up the drive after installing XP? I'm guessing 64MB should be adequate.

**Swap** - I know, I know, it's always being asked, but I've got 1GB RAM and I can't find any definite answers for this one. Most sources state you should generally have 2x RAM as swap space, whereas some say if you have 1GB RAM then you shouldn't need any. Another view I've encountered is 2x RAM or 512MB, whichever comes first. Bearing in mind that I won't be playing Unreal Tournament and compiling OpenOffice simultaneously, what would you recommend? I've considered a swap file, but I'd like to keep things as simple as possible while starting off. :)

---

### Post by starcraft.man on 2007-05-12
> **AlfAlf said:**
> Thanks for that ext3 driver link, undertakingyou, that looks better than the other ones I've come across.



That's really good news actually, as I wouldn't have enough space at the moment to shuffle everything about during reformatting. So I'll keep it as NTFS for now, I can always move it over if I drop Windows completely, by then I'll probably have a larger SATA drive when I eventually get a new mobo.


Right, just got a couple more questions regarding the more "essential" partitions, then I think I'll be ready to make a start...

**Boot** - Will this be created during the install, or will I need to allocate space for it when I slice up the drive after installing XP? I'm guessing 64MB should be adequate.

**Swap** - I know, I know, it's always being asked, but I've got 1GB RAM and I can't find any definite answers for this one. Most sources state you should generally have 2x RAM as swap space, whereas some say if you have 1GB RAM then you shouldn't need any. Another view I've encountered is 2x RAM or 512MB, whichever comes first. Bearing in mind that I won't be playing Unreal Tournament and compiling OpenOffice simultaneously, what would you recommend? I've considered a swap file, but I'd like to keep things as simple as possible while starting off. :)

You don't need to do anything in the install or partitioner to set up the boot, GRUB will install itself to the MBR unless you specify otherwise, its best to use GRUB its a good bootloader.

I can only really say about Swap that even if you have 1 gb or ram you should have some swap, I guess I'd qualify is being a 2X person, since I got 2 GB. I don't really see how adding a swap can make the partition more complex, Ubuntu really only needs a Root (/) and swap, thats it, and a home folder if you want it.

---

### Post by AlfAlf on 2007-05-12
> You don't need to do anything in the install or partitioner to set up the boot, GRUB will install itself to the MBR unless you specify otherwise, its best to use GRUB its a good bootloader.

Yeah, it was a choice between that and LILO, but I've heard that can be a bit temperamental.

I've heard that XP might complain if there isn't a windows bootloader present in the MBR. I'm just a bit concerned about screwing everything before I've even really started, so I might use Partition Magic to create a boot partition anyway. Safety first and all that.

Anyway, thanks very much for all your help and advice everyone, I really do appreciate it. I'll probably be back later on this evening when I break something! :lolflag:

---

