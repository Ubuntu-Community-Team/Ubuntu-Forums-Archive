---
title: "Ubunto 6.10"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by trachycarpus on 2006-11-10
Ive just downloaded this a I want to make my first foray into Linux. What a pity that the live CD dosn't save my settings so I can do an extended test without having to reset everything. However I suppose the best way to check it out is to install it. My problem is that I currently run only WinXP (accounts package etc) and will need to dual boot. I have no experience with this so some assistance before taking the plunge would be appreciated. 
My comp was set up by a 'friend' who set it up with C split into 4 partitions, 2 of which are free and are ntfs. The second drive is set up as active with xP on it. 
If I get Ubunto to install will it leave windows alone and install onto the spare partition 'E' (15gig)? 
Will I have to reformat E to fat?
If not where can I find the best way of installing this, bearing in mind that although I am a fairly experienced normal user this is the first time I've plucked up the courage to try a dual boot.
Sorry for the long and rambling post but I hope someone can help.
Peter

---

### Post by bikeboy on 2006-11-10
Don't worry, everyone is a little nervous the first time they do partitioning. It's probably advisable to backup anything that's really important to you, even though it's easy to set up the drives if you read the instructions.

The LiveCD installer will list each of the partitions on your hard drives once you get into it, there will be a tick box on each one where you select whether you want to reformat it or not. Make sure your windows drive is unticked, along with any others you want to leave alone.

Then setup a / partition and a swap partition (1 gig or less) to your liking and you're set to go. Ubuntu can format to several filesystems, ext3 is the default and the best option to begin with. When you're more comfortable with it all you can even install with a separate /home partition so that you can upgrade to new versions of Ubuntu while easily keeping all you files and settings.

---

### Post by Sef on 2006-11-10
Read this to [Dual Boot]("http://www.psychocats.net/ubuntu/installing") from a Live CD.

Recommended to read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/"), which talks about dual booting from the alternate cd.  However, there is a lot of useful information there on pre- and post-installation.

---

### Post by rlozano on 2006-11-10
> **trachycarpus said:**
> Ive just downloaded this a I want to make my first foray into Linux. What a pity that the live CD dosn't save my settings so I can do an extended test without having to reset everything. However I suppose the best way to check it out is to install it. My problem is that I currently run only WinXP (accounts package etc) and will need to dual boot. I have no experience with this so some assistance before taking the plunge would be appreciated. 
My comp was set up by a 'friend' who set it up with C split into 4 partitions, 2 of which are free and are ntfs. The second drive is set up as active with xP on it. 
If I get Ubunto to install will it leave windows alone and install onto the spare partition 'E' (15gig)? 
Will I have to reformat E to fat?
If not where can I find the best way of installing this, bearing in mind that although I am a fairly experienced normal user this is the first time I've plucked up the courage to try a dual boot.
Sorry for the long and rambling post but I hope someone can help.
Peter

please feel comfortable trying it out. and during the installation process, be careful reading all the instructions, and familiarize yourself with the hdxx phrase so you will be able to identify which one is your window drive.

but most important, before proceeding so, make a backup of all your important data in your windows installation. so even if you screwed it up,you still have your backup.... 8)

---

### Post by trachycarpus on 2006-11-10
Thanks everyone for the help. I'll start backup tonight to an external H/disk. Then pour a strong cup of coffee and read all the links and see about installing. 
I assume the install of Ubunto can go on any partition and not necessarily on the active one like windows. 
Regards
Peter

---

### Post by Bartender on 2006-11-10
If you want to take this one step at a time, I'd suggest downloading [GParted]("http://gparted.sourceforge.net/livecd.php") LiveCD (this can be done on a Windows PC) and burning it to a CD.  This creates a bootable CD that gives you a great window into your partitions.  
The GParted CD is a more powerful tool than the version on the Ubuntu LiveCD.  But for people who just want to use the basic features, it's essentially identical to the partitioning step of the Ubuntu LiveCD.

You say you have 2 partitions that are unused?  Unless you have plans for them (such as maybe installing another Linux distro) I'd suggest using GParted to delete one of them, then expand the adjacent partition so that you end up with just one.  Apply the changes, then get out and put in your Linux CD.

Some folks would say there's no sense in doing it this way, because you could do the partitioning with the Linux LiveCD.  The only reason I suggest this is to slow things down a little bit, and build some familiarity.  If you do it all from the Ubuntu CD, your brain might be going into vaporlock from the stress.

---

### Post by freebeer on 2006-11-10
Would it not be better to just add a second hard drive to the system, then install it on the new drive?

New drives are pretty cheap and I'd think you'd greatly reduce the risk of messing up your Windows hard drive.  (and Windows, which has a tendency to assume it's the only thing on your machine, won't mess with your Linux drive.)

---

### Post by CatKiller on 2006-11-10
> **trachycarpus said:**
> What a pity that the live CD dosn't save my settings so I can do an extended test without having to reset everything.

Actually, if you think about it, it's better this way. You can try out the live cd without **anything** happening to the hard drive - nothing gets saved, nothing gets stored. It's a comfort to those who are very nervous.

Good luck with the install, and welcome to the community.

---

### Post by infoseeker on 2006-11-10
My first attempt at Linux was to go out and buy a new harddrive and connect it as IDE2 primary. I then (using CMOS setup) changed this drive to the primary boot drive, and installed Linux onto it.
It was then a matter of reversing this (CMOS) setup when I needed to get back to the original setup.

---

### Post by trachycarpus on 2006-11-10
Thanks for the replies
I already have a 40 gig split to 4 partitions, not my doing a paranoid friend did this to make sure I have a copy on a separate disk to boot from incase of trouble. The second disk is also 40gig (k) which is the active windows partition.
I've backed up the K drive to an exrernal 40gig drive.
Will download Gparted and combine the two unused partitions, reformat them to fat and try to install ubunto onto this.
Probably not tonight as its a bit late if trouble rears its ugly head.
If I, in future, wish to try another distro I assume I would have to make another partition for it.
Peter.

---

### Post by wavetheory on 2006-11-10
> **freebeer said:**
> Would it not be better to just add a second hard drive to the system, then install it on the new drive?

New drives are pretty cheap and I'd think you'd greatly reduce the risk of messing up your Windows hard drive.  (and Windows, which has a tendency to assume it's the only thing on your machine, won't mess with your Linux drive.)

That was the conclusion I came to this past summer when installing 6.06 (and my first time installing Linux) on my Dell desktop machine.  Ran down to the local computer store, bought another HD, installed it, set up quite a few partitions on it, and installed Dapper 6.06.  So now I have a nice extra drive that I can mess around on in Ubuntu (and Kubuntu) and not worry about the integrity of my other drive with WinXP that my family uses for stuff like Quicken and other Windows apps.

---

### Post by trachycarpus on 2006-11-10
I have just downloaded(twice) a copy of Gparted as suggested. It started to go through its paces, got to the end and then went into a blank screen, over 5mins, and nothing happened. I assume theres a compatibility problem, or should I have waited longer?
Looks like I'll just have to read some more and jump in at the deep end. I hope I can swim far enough.
Peter

---

### Post by Ocxic on 2006-11-10
if you already have a partiton you would like to use, as u mentioned the E drive you can go ahead and use that, ubuntu will leave windows alone, and if you have a partiton with the disk lable set as "casper cow" the live cd will save your settings.

---

### Post by kinematic on 2006-11-10
don't format it to fat....that's not a native linux file system.
stick with ext3 wich is the default.

---

### Post by xpod on 2006-11-10
And as i was reminded on many an occasion the names "ubuntU".......:mrgreen: 

Dont be put off by any hitches you come across m8 as they can sometimes be part and parcel of the deal to start out....All part of the fun.:D 

It`s sometimes just a case of finding the right method and iso for ones own particular setup...The alternate cd`s can save a lot of frustrations but obviously you cant "try" Ubuntu out as you can with a "live cd".

Im sure these good folks will have you up and running in no time regardless!
Good luck m8 and welcome to THE machine;)

---

### Post by trachycarpus on 2006-11-11
Yippee I've done it, I'm now live with a full install. Phew!!!! Much easier than I thought. The new installer, compared to the guide which was very useful,,is much cleaner. Mostly automated, just like windows. Where's the icon for "spits in corner"?
I have yet to configure the printers, I use 3, Oki320 for plastic labels, Canon Pix4200 for piccies and Brother Hl2030 laser for general purpose work. Such a pity that Sage do not do a version of their accounts software for Linux.
Peter

---

