---
title: "Linux complicated for average user? (Need help partitioning/installing)"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by odoyle on 2007-04-08
So I went to install Ubuntu and was very excited about doing so.  I'm tired of my Microsoft crap and am ready to get into a secure and true system.  Anyways... I'm fairly good on Windows... but am abolutely new to Linux... so some parts on the installation scared me.  The only two options on the hard drive partition were either... delete your whole hard drive... or manually partition drive.  I need to keep my Windows OS and also the data... but do not know how to manually partition my drives and don't want to delete data on accident.  I tried the manual partitioning, but it wasn't cake either... at least to me.

Then I went on a bunch of Linux help sites trying to get an answer, but everyone is talking in a Linux language that I can't understand!  Even certain aspects of this starter forum are confusing to an experienced Windows user.

Can someone please walk me through this partitioning thing?  I really don't want to delete my whole hard drive and all data.  Thanks! Look foward to getting up on Linux (and understanding the funky language I see on this and other forums:) )

---

### Post by bashologist on 2007-04-08
Some people might say resize your hdd, but I wouldn't advise that. Do you have a full extra hdd? Then maybe lookup a way to backup your mbr just to be safe.

---

### Post by moffa on 2007-04-08
You have to first resize your windows partition.  This can be a learning experience.  I think gparted would do the job.  You can download the livecd version from:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

After that you should be able to select Use largest free space.  Good luck

---

### Post by atbnet on 2007-04-08
I agree that the ubuntu partition manager isn't very good for maintaining previous sets of data with the manual partition function. I've been bitten before so I play it as safe as possible and use a different drive or an entirely different computer if possible. The mbr monster has gotten me too many times.

---

### Post by aysiu on 2007-04-08
The only way to be 100% sure you don't delete your data is to **back it up**

If you know what you're doing, you can usually be about 99% sure you won't delete your data.

Since you don't know what you're doing, it's probably more like a 50% chance, so **back it up**. If you don't have the means to back up everything on your computer that's important to you, I would strongly advise against setting up a dual boot right now. Run the Desktop CD (also known as the "live CD") for several weeks. Get more accustomed to Ubuntu.

Some human-readable guides for you:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by odoyle on 2007-04-08
To be honest... I'm on a fairly new computer so the data isn't all that important yet.  Most of it I already have backed up.  I'm just concerned that if I give the whole hard drive to Linux that I won't be able to function.  It's going to take me a while to get up and running on Linux and I want to be able to use the programs and functionality I'm used to.

---

### Post by aysiu on 2007-04-08
> **odoyle said:**
> To be honest... I'm on a fairly new computer so the data isn't all that important yet.  Most of it I already have backed up.  I'm just concerned that if I give the whole hard drive to Linux that I won't be able to function.  It's going to take me a while to get up and running on Linux and I want to be able to use the programs and functionality I'm used to.
Then use the live CD for a few weeks. Get used to using the programs and the interface before you commit to an installation. That's one of the beauties of the Desktop CD. It can run from your computer's RAM without affecting your computer's hard drive. It gives you a fully functional Ubuntu operating system--completely risk-free.

---

### Post by atbnet on 2007-04-08
I would use a partition manager and divide up your hard drive how you want it. Make sure Windows is on there first and just make some room for your ubuntu install. It seems to work better in that order in my experience. Still, I'm not a fan of splitting up a drive with more than one OS. I've nuked myself more times than I wanted to.

---

### Post by odoyle on 2007-04-08
Got ya.. and will do!  One initial problem I'm having with using the CD is that I'm not able to wirelessly connect to the internet.  With Windows my machine esentially finds the wireless networks for me... and I just click on one.  How do you connect to the internet wirelessly on Ubuntu?  Thanks much for your help!

---

### Post by kahrytan on 2007-04-08
There is one safe way to instal Ubuntu. Buy a second hard drive. The now standard 80gb is fine.  You can keep Windows in the meantime. You might run into a problem and need it.

---

### Post by Hieronymus on 2007-04-08
When you are confident enough to throw away  your windows and ready to give your whole disk to the penguin you could do the following, I'll first say someting about the basics.

There are three things important to know when making partitions:
The size:
[INDENT]To change the size in the partition manager used in the installation process you can just type something like +20GB to make a 20 GB partition. You type this in the end box. For swap just take 2 times your physical memory. So if you have 1 GB memory take +2048MB swap.
[/INDENT]The mountpoint
[INDENT]For linux the mountpoint is important, this is where you can reach the partition in the linux system. 
/ = root. 
/home = where you personal settings are kept. 
/boot = Where all essential information for the boot proces is placed
swap = something like the windows virtual memory. 
If you don't create a seperate partition for /home and /boot all this info will be placed on the /.
/userfiles = a mountpoint I always create to put my downloads and documents in. I like to keep what I don't want to lose seperate from any settings. 
[/INDENT]The filesystem
[INDENT]If you want to make a separate boot partition this has to be in the filesystem format ext2. 
For the swap you must just chose swap
For the rest you can chose for instance ext3 or reiserfs. ext3 is most common. 
[/INDENT]There is more, but these are most important. This is the possible config:

I just assume you have 100GB of hdd.
[LIST=1]
[*]mount point: /boot, size: 32MB, file system: ext2.
[*]mount point: /, size: 20GB, file system: ext3
[*]mount point: /home, size: 5GB, file system: ext3
[*]mount point: swap, size: 2x physical memory, file system: swap
[*]mount point: /userfiles, size: whats left, file system: ext3[/LIST]It's just a suggestion, good luck

Jeroen

---

### Post by Gina on 2007-04-08
Firstly, I agree with the others - run the live CD and get used to fiddling with Ubuntu.  I presume you have just the one computer and are afraid to lose your Windows system - I can well understand that.  Although I have been using computers for years, I'm still a bit afraid of messing up and losing contact with support on the net.  Getting wireless adapters working can be tricky in Linux generally, though Ubuntu seems pretty good in that respect and has direct support for several wireless adapters, meaning they work straight off.  Ethernet (wired) adapters have very much better support and most will connect immediately. So if you can connect directly to your router by cable, that should work.

If possible I would suggest getting an oldish secondhand PC to play with.  That way you are sure of not disabling your main PC.  OK, I know that means money and one of the main points of Linux is that it's all free but sometimes it's worth spending a little money.

I'm on the point of writing an absolute beginners guide to partitioning but not had time yet.  I agree that many of the guides, though good, are not really (and I hate to put it this way as I think it could be insulting) "dumned down" enough for the real newbie.  Most more experienced computer users find it very difficult to do this.  I have successfully resized where Windows lives and installed Ubuntu as dual-boot with Windows.  You have to do it manually as the installer is still a bit lacking in this respect, even with the lastest version.

In conclusion and before I rabbit on any more....  Try and get familiar with Ununtu with live CD first and we'll come back to installing later.  Good luck :)

---

