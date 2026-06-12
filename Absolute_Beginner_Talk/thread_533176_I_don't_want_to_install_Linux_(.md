---
title: "I don't want to install Linux :("
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Anders Moen on 2007-08-23
Hi

For a long time I have been wanting to install Linux (Ubuntu) but a friend of mine did and he lost everything on his computer including Windows itself

So..well, should I anyway? I really don't want to loose everything on my brand new computer with Vista

---

### Post by Raineer on 2007-08-23
Follow the directions carefully.  When you choose to partition the drives be sure to use the manual option, or at least do this step VERY carefully and understand what you're choosing. That way you won't lose windows.

Installing Linux *after* windows is installed is the best way to do so and maintain dual-boot status.

---

### Post by pgar23 on 2007-08-23
> **Anders Moen said:**
> Hi

For a long time I have been wanting to install Linux (Ubuntu) but a friend of mine did and he lost everything on his computer including Windows itself

So..well, should I anyway? I really don't want to loose everything on my brand new computer with Vista

BEFOR YOU DO ANYTHING CHECK OUT MY SIGNATURE FOR DUAL BOOTING> SAVE YOURSELF THE PROBLEMS.

|
|
|
V

---

### Post by Lord Illidan on 2007-08-23
Also make backups!

---

### Post by jingo811 on 2007-08-23
**Anders Moen>>>**
Do you have a Windows Vista full installation CD/DVD that installs Vista from scratch?
Or did your Vista recovery CD/DVD come **bundled** 	[-( with your PC/laptop along with predefined partitions and driver setups?

**pgar23>>>**
> BEFOR YOU DO ANYTHING CHECK OUT MY SIGNATURE FOR DUAL BOOTING> SAVE YOURSELF THE PROBLEMS.
Did you make that awesome Vodcast?  I've seen it before it's good the only drawback is that it doesn't have a better resolution.  If it only had at least 640x480 resolution it would be the BEST tutorial in the world.

---

### Post by r4ik on 2007-08-23
Try,

[http://www.pro-networks.org/forum/about78184.html#dualboot](http://www.pro-networks.org/forum/about78184.html#dualboot)

Good luck !

---

### Post by pgar23 on 2007-08-23
> **Lord Illidan said:**
> Also make backups!

GOOD POINT! wutever you do, make backups! I made this mistake(once or twice, or maybe 5 times :)) 
FOR YOUR SAKE MAKE BACKUPS!

---

### Post by Aishiko on 2007-08-23
I was going to respond "then don't!" but your concerns make sense, (I guess, I've tried Vista and frankly I'll stick with XP Pro it's much faster on the same hardware and easier to navigate thru.)

But follow the directions and read as much as you can on the process of adding Linux to a computer.  And you should be fine.  If your very concerned about it, ask a friend that knows alot about Linux and has set up a dual boot system before.

---

### Post by stinger30au on 2007-08-23
you can run Linux inside of XP, get a copy of [Virtualbox]("http://www.virtualbox.org/")

---

### Post by Anders Moen on 2007-08-23
Whoa! That was many replies in a second ;p

Anyways, I'm not sure how I make backups

No, the Vista install cd was not included..it was installed from before

Ok, I will try that guide r4ik

---

### Post by jingo811 on 2007-08-23
> No, the Vista install cd was not included..it was installed from before
If Vista was pre-installed when you purchased your PC then you should have some sort of license paper from Microsoft. 
If so it's go time.  I want to see if someone can actually turn down the EULA agreement and get the money back so you can buy a full Windows XP installation CD instead or Vista if you must have that snailware.


> In some cases the user can return Windows for a refund by refusing to agree to the Microsoft End User License Agreement that Microsoft requires its users to accept before allowing the use of several products. The EULA specifically mentions that if you do not agree to the license you can return the product for a full refund. Some vendors, such as Toshiba, have a shrinkwrap sales contract that specifically voids this clause of the EULA. 
**source:**
[http://en.wikipedia.org/wiki/Criticism_of_Microsoft#Licensing_agreements](http://en.wikipedia.org/wiki/Criticism_of_Microsoft#Licensing_agreements)

---

### Post by pgar23 on 2007-08-23
> **Anders Moen said:**
> Whoa! That was many replies in a second ;p

Anyways, I'm not sure how I make backups

No, the Vista install cd was not included..it was installed from before

Ok, I will try that guide r4ik

B4 trying the guide from r4ik, i recommend you check out my signature for the dual boot tutorial, not to shun r4ik's reccomendation, but the tutorial in my signature is a VIDEO TUTORIAL on google video, and it is one of the most simple tutorials I have seen on dual booting, trust me.

---

### Post by armandh on 2007-08-23
I did 2 other solo installs B4 trying a dual boot and I repartitioned the drive with a utility that has a visual display of what I was doing. once I had the necessary unpartitioned space I installed using the option "use unpartitioned space" worked fine. back up always

---

### Post by Bethrine on 2007-08-23
I installed Ubuntu after a pre-installed Vista. I found (using Ubuntu) Vista already had a backup partition 12 GiB big (dev/sda1) on it (SATA drive) followed by my Vista partition (dev/sda2). I, unfortunately, didn't do my homework and follow the directions for partitioning and have somehow messed up my Vista, :(  Stupid me  ](*,)

*edit* to get the dual boot running with Vista I had to tweak grub a little bit too.

---

### Post by pgar23 on 2007-08-23
> **Bethrine said:**
> I installed Ubuntu after a pre-installed Vista. I found (using Ubuntu) Vista already had a backup partition 12 GiB big (dev/sda1) on it (SATA drive) followed by my Vista partition (dev/sda2). I, unfortunately, didn't do my homework and follow the directions for partitioning and have somehow messed up my Vista, :(  Stupid me  ](*,)

Did you solve this dilema and you are offering advice for him or are you suggesting you have a similar problem? If you have a similar problem as this I think you should just follow this thread until this is solved.

or if you are offering advice, be more specific on how to solve this problem.

---

### Post by Bethrine on 2007-08-23
lots of posts while I was typing, was referring to the prior post about backing up just trying to help sorry

butting out now  :blush:

---

### Post by LowSky on 2007-08-23
just a feww steps of the top of my head

1st defrage your hard drive in vista
2nd back up everything if you can
3rd partition a small amount of your hard drive for linux dont go to big 15Gb is good
4th go slowly


or ask a friend if they have and old hard drive and swap out the one you have for thiers, or buy new extra hard drive and swap out

this way you dont mess up windows and you dont have to partition anything

---

### Post by Delkster on 2007-08-23
I installed Ubuntu (7.04) on my work laptop that had Vista pre-installed. No problems. Of course I've also been running Linux since 2001 or so, so I may have instinctively done some things or tweaks that someone without Linux knowledge doesn't know about...

Anyway, there are basically two things that can be more or less risky in installing an operating system (Linux, or anything else really) for dual-booting with your existing Windows system. The first one is partitioning, and the second one is installing the bootloader that is used to load Linux.

I don't know how much you know about PCs and computers in general, so sorry if this sounds way too basic, but the hard disk is divided into partitions. Your Vista setup has at least one of them, and it shows up as your C: drive. It may also have other ones. Linux will also need one of its own, at least one but preferably at least two.

The problem is that all space on your hard disk is very likely allocated to the partitions that are used by Windows. Thus, you need to somehow free up space from those partitions in order to be able to create a new one for Linux. This is not the same as freeing up space on your Windows partitions -- even if you delete files or whatever to get more free space, the physical storage space on your disk is still allocated to the Windows partition.

Thus, in order to get some room for the Linux partitions, you need to either delete some of the existing partitions or shrink one of them to get some disk space that isn't allocated to any partition. You can then create the Linux partitions within that unallocated space.

Information about what partitions you have and some other details about them are stored in a partition table on the disk. Modifying the partition table, which is obviously necessary if you want to create a new partition, is inherently a little risky: if something goes wrong with the modification, the computer may no longer be able to find the partitions even if the data is still physically there. This is, however, pretty safe nowadays; the tools that come with Ubuntu deal with it just fine.

The riskier part is the deletion or shrinking of existing partitions. If you have several partitions showing up as separate drives in Windows (for example C: and D:, both hard disk) and you have no use for the D: drive, you could delete the partition holding the D: drive and use the space for Ubuntu, without touching C: and thus keeping it pretty safe. Obviously, if you delete the wrong partition... well, it'll be a little difficult to access the data stored on that partition afterwards. (The data is still physically there, the system just doesn't know where to look.) If you can't or don't want to delete any existing partitions (e.g. if you only have one partition for Windows), you can also resize an existing partition to make room for Ubuntu.

You can do that with the tools that come on the Ubuntu Desktop CD, but at least some versions of Vista actually come with partitioning tools that allow you to resize existing partitions. I used the Vista tools to shrink the Windows partition, after which I had enough unallocated space on the drive to install Ubuntu. After that I just booted from the Ubuntu CD and ran the installer. The only thing the installer had to do regarding the partitions was to create the Linux partitions within the unallocated space. In the installer the automatic partitioning option that uses the largest free space works just fine for that. Just make sure you don't choose something like "Use entire disk" instead -- that'd wipe your Windows partitions.

That way, the risky part -- resizing the existing partitions -- was done with the Windows tools, and I'd imagine that the tools that come with Windows would be able to handle its own partitions. At least I ran into no problems. You can also do the resizing either within the Ubuntu installer or with other tools that come on the Ubuntu Desktop CD, but I chose to use the tools that came with Vista. They're somewhere in "Control Panel > System Tools" or something like that -- I can't remember exactly and can't check now. Of course, the Vista version that my work laptop has is a business edition, so I don't know if the home editions come with those tools. If not, you just need to use some other tools, such as the Gnome Partition Editor that comes on the Ubuntu CD (found in System > Administration) or the installer itself.

The other potentially risky part that I mentioned was the boot loader installation. At the end of the installation process Ubuntu installs a bootloader called GRUB. It has a boot-up menu where you can select which operating system you want to start, and the Ubuntu installer automatically detects your existing Windows system and adds it to the boot-up menu. On the other hand, if something goes wrong with installing the bootloader, your system may no longer boot at all. That's not quite as bad as it may sound, though, because your data and the Windows system and everything is still there; the system just can't find it, and all you need to do in order to boot the system is to somehow fix the bootloader. There are tools for that, so nothing will be permanently lost. In any case, losing your bootloader is quite unlikely, and as I said, it's quite possible to recover from that even if it does happen, so I wouldn't worry about that.

This is quite long a post, but hopefully it clears up a little about what is risky about operating system installations. Just be careful when editing your partitions with any tools and you should be fine. That's clearly the riskiest part of the whole thing, and it's quite unlikely that anything bad will happen there either. Don't delete the wrong partition. ;-)

---

### Post by jingo811 on 2007-08-23
eek :shock:

---

### Post by LowSky on 2007-08-23
Delkster knows just how to scare someone away from using linux...lol

I suggest you only do something if you truely dont care about the risks... remember without risk there is never any gain. So in relative terms, take a chance!!! You'll love it the adrenaline rush!

---

### Post by mikex on 2007-08-23
Get a good disk *imaging* program like Acronis - I live and die by it at work. It will make an exact image of your HD - XP,Vista, or Linux, sinlge or dual-boot onto an external USB or another internal HD. Make an image before any major change, that way you can get back what you had like magic with the bootable CD you can make with it. Acronis costs about $25 or so and worth every cent. I have been making images of Ubuntu before doing things since I am not sure of linux yet, and it has already saved me a lot of work. Go ahead and mess up your system, it won't matter because you can get it back in a few minutes.

---

### Post by Aishiko on 2007-08-23
> **mikex said:**
> Get a good disk *imaging* program like Acronis - I live and die by it at work. It will make an exact image of your HD - XP,Vista, or Linux, sinlge or dual-boot onto an external USB or another internal HD. Make an image before any major change, that way you can get back what you had like magic with the bootable CD you can make with it. Acronis costs about $25 or so and worth every cent. I have been making images of Ubuntu before doing things since I am not sure of linux yet, and it has already saved me a lot of work. Go ahead and mess up your system, it won't matter because you can get it back in a few minutes.
excellent adcice.

---

### Post by gerry1936 on 2007-08-24
If you just want to get a taste of Linux, download something quick and small that you can run as a Live CD- ie it does not install. I used Puppy Linux- it boots from the CD just as quickly as a big heavyweight distro from hard disk. Puppy saves your set-up info and any files you create in a "save" file, which it puts wherever it can find a little room- ie it does not need its own partition, and does not need a Linux filing system. Dead easy! But limited.

If it whets your appetite for bigger things, then that's when start worrying about all the partioning, dual booting, etc.

---

### Post by bliffle on 2007-08-24
What I'm doing is copying the old windows system to a new HDD then applying ubuntu to this new HDD. The old HDD becomes your backup.

---

### Post by daveshields on 2007-08-24
This issue is not so much that you don't want to install Linux, but that in doing so you don't want to risk destroying any data on your hard disk.

The easiest way to avoid this risk is to install Ubuntu on a separate disk. If you don't have an old one at hand then you get a good disk with 250 GB or so for about $50 from newegg.com . Take out your Windows hard disk,  put the other one in and do a full install of Ubuntu. 

If you decide you don't want to continue using Ubuntu then you will have a free disk you can use with your existing system.

If you want to continue using both Windows and Ubuntu you could then do a dual-boot install on your existing Windows disk. By that time you would have gained the confidence to attempt this.

---

### Post by irish_flu on 2007-08-24
> **Anders Moen said:**
> Whoa! That was many replies in a second ;p

Anyways, I'm not sure how I make backups

No, the Vista install cd was not included..it was installed from before

Ok, I will try that guide r4ik

Sorry I'm late to the party here, but this post stuck out to me.  Before you decide to start playing with Linux, and even if you decide not to, learn how to back up your stuff (burn it to a CD/DVD, get an external hard drive, etc).

If you have stuff you care about, make a backup- Period.  That goes for Windows, Linux, OSX, anything.  The best OS in the world won't save you from a broken hard drive, a lightening strike, a carefully spilled beverage, or an itchy delete finger.

To reiterate, by all means install Ubuntu and have fun; however, it's far more important that you learn how to back up your stuff first.

---

### Post by Jored on 2007-08-24
I think some excellent advise is contained in this thread.

I started off from a Feisty Fawn DVD that came free with a magazine, trying to bring life back to an old Dell Latitude LS400 (Pentium 3, 400Mhz, 256MB, 40GB HDD).

I followed mikex's advise: made an image of my Widoze2000 installation plus data onto an external USB HDD with Acronis. Great product and it allows you to recover your original system in minutes if anything goes wrong.

Then I installed from the LiveCD, just as Delkster very clearly and realistically advises.

And that was all it took. Worked first time, no data lost, and dual boot worked fine, so I could spend my time tuning Ubuntu and adding applications.

I don't think I'll be doing much in Windows in the future. My old laptop took 12-14 minutes to boot Windows 2000. It now takes 90 seconds to boot Ubuntu. And for normal internet stuff, email, viewing/editing photos, etc, it is as fast as my brand new Dell Dimension 9200 with a dual core 2.67Gz procesor, 4GB memory, 1TB raid1 HDD array and Vista Ultimate. Granted, no gaming nor sophisticated graphics, etc.

Go ahead. Do it. You'll never regret it.

---

### Post by Anders Moen on 2007-08-26
Ok, thanks for the tips everybody. I haven't got to read everything, because this is way too much to read in this short time but thanks ;p

---

