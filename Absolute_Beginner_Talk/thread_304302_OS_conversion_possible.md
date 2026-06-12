---
title: "OS conversion possible"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by dragon-architect on 2006-11-21
--Warning-- loooong post --Warning-- (you have been warned)

After a [roughly 15-20 yr.] lifetime of frustrating experiences, I've had it with Windows. For the fourth time in the past six months, my laptop's OS has collapsed on me while working on a project, and I have been forced to waste money taking my computer to the pros to have it troubleshooted, or had to wait a half hour for my laptop to recover.

I have a little experience with Mac mostly because of two teachers that work in the same building my mom does who have nothing but Macs. However, I don't want Mac--my laptop isn't optimized with Mac-compatible hardware anyway. So, I went to my favorite computer repair shop to ask them about Ubuntu. One of the salesmen rebooted one of their laptops-for-sale from the CD drive and let me play around with Ubuntu for a few minutes, and I loved it, and I really loved the desktop.

Originally, I had plans to wipe out half my savings account on building an external hard drive, which really is cheaper than buying one premade (I priced parts myself), on which to back up all my files. Then today, I hit across the idea of running a dual-bootable system on my [AMD Athlon 2200 XP powered] laptop with Windows XP and Ubuntu until I have everything set just the way I need it. Of course, I want to avoid going straight to Ubuntu because I have Windows-only compatible computer games and programs that I have no idea where the individual files necessary for proper operation go.

So, I have one question that maybe a bit n00b-ish, but I'm not what you would call a computer geek:  Would it be possible to share files over a partition boundary in a hard drive? The reason I ask this is because this is THE very first time I have thought about partitioning a hard drive, or converting a computer to an OS that did not originally come with it.

Also, a friend on a chatroom who has very recently switched to Ubuntu has warned me that the Dapper installer is bugged somehow so that it cannot complete the installation, and that Edgy has some pretty nasty bugs. He told me to find a version of Breezy Badger and manually upgrade to Dapper. Is the Dapper installer still bugged, or is what he told me good advice?

I know it'll be a long and frustrating process switching to a new OS, which is why I'd prefer a dual-bootable system for at least the first few months or however long it takes to get Ubuntu configured to my final preferences. Also, part of the reason I want to run a dual-boot system for the time being is because of my laptop's accessibility to the internet, which is not guaranteed, but generally very high during the weekends when I can get close enough to a wireless router.

At any rate, if I could get some advice pertaining to a recommended version of Ubuntu, I would greatly appreciate it. Please keep in mind I don't have much patience with software, so I'd prefer something with as few bugs as possible.

Phew! What a lungful! *faints*

---

### Post by bulldog on 2006-11-21
Download the Dapper Drake live cd and boot from it to see if your laptop will run with the cd.
If your hardware is properly recognized on the live cd,you shouldn't have any trouble installing it.

---

### Post by annda on 2006-11-21
aye, dapper it should be. some laptops run the live cd fine but have trouble installing because of the video/graphic driver (i've had this a long time ago with breezy), but i don't know if it's still the case. if it is, check out the forums for the appropriate installation option (vga=771 or something, sorry, it's been a long time).

the only other problem might be your wireless internet connection - i would highly recommend running the live cd on a weekend and testing the connection with that router you've mentioned.

good luck!

---

### Post by glotz on 2006-11-21
I didn't believe your warning and ended up reading the entire post! Whoa!

First of all, your plan is very good. The road might be long and winding but don't give up. Your freedom is well worth it.

Here's the deal with filesharing. Ubuntu can read FAT16, FAT32 and NTFS partitions. It however cannot write NTFS out of the box. Windows cannot read Ext3 nor Reiser as far as I know. So you need a FAT(32) partition so that both OSes can read and write it. Then again, there's a remote chance that your disks are already FAT32.

I couldn't install Dapper from the default CD. Installed breezy and upgraded online. Dunno what that was all about. I suggest you try Dapper rather than Edgy.

I used to dual boot a few months. Then I realised that I never seemed to use windows anymore. Then I regained the diskspace. I've seldom felt so good... :)

Be bold and do it. And when you'll have questions, we're right here for them.

---

### Post by dragon-architect on 2006-11-21
Where can I find the Dapper CD? I didn't see any links for it on the website at first glance. If I can't get it here, I've got a friend that can send me the installer.

I just checked my computer. It's NTFS. Man, that's screwed up! Windows is gettin' too smart. Okay, now my job just got that much harder. :( 

Well, the official numbers are thus:
55.8GB total
19.3GB used
35.5GB free

I've got plenty of spare room for a FAT32 partition. It only has to be maybe no more than 5-10GB because the only games I run are SimTower, SimCity4, and Roller Coaster Tycoon 2. SimTower I know has reference files in the System and System32 folders on the computer (made for a bit of trouble on initial installation due to an unlocatable file). However, I dunno about the others. I'll have to ask somewhere where ppl are familiar with the games.

As for my graphics card, there's nothing much I can do to change its settings. It's integrated into the motherboard because I've got a tiny li'l laptop. The thing's lighter than my textbooks! Oo

---

### Post by NiklasV on 2006-11-21
There is an ext2 driver for windows, and it works for ext3 as well, although it doesn't have support for journaling (journaling logs changes to the file system, preventing corrpution in case of a crash)
It's called Ext2 IFS: [http://www.fs-driver.org/](http://www.fs-driver.org/)

There's also Explore2FS, which is a file handler for ext2/3 filesystems: [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

The best option for full read/write support though is to have windows on a fat32 filesystem. But if you don't feel like reinstalling windows (it can be pretty daunting to find all the required drivers if they weren't included on separate discs), you could go with the previous alternatives.

As for which version to choose, I agree with the previous posts, go with Dapper, it's the "long term support" version and is what people without alot of computer knowledge should choose.

The wireless may work out of the box depending on your chipset. If you have an intel chipset, which is very common for the integrated wireless in laptops, it shouldn't be a problem. Otherwise you can usually use ndiswrapper (a utility which wraps around windows drivers for use with Linux) to get it up and running.
You can check [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) for a list of wireless cards and their status.

Network manager is great for wireless if it supports your driver, it can be installed with synaptic, or with automatix. ([http://www.getautomatix.com/](http://www.getautomatix.com/))

You can get the Dapper CD here: [http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)
It's under Ubuntu 6.06 LTS (Long Term Support)
Burn at the lowest speed available, you don't want to risk any corrpution of the disk, this has happened to me several times when I've burned the ubuntu cd at high speed.

---

### Post by dragon-architect on 2006-11-21
Uhhh... Niklas, I'm not a computer geek. Your first two paragraphs went waaaaaaaay over my horns. O.o

I don't want to reinstall Windows. That'll mean losing all my files from what I understand, and reformatting will definitely do that. I don't want that. Not only that, but I lost my system restore CD for my laptop, and I want to save as much money as possible.

Thanks for the Dapper link. n.n;

---

### Post by wpshooter on 2006-11-21
Dragon:

I don't recommend dual booting your computer.

My advice would be to find yourself another cheap laptop or desktop computer and load Dapper (from the DESKTOP CD) and experiment with it for a few weeks and see if it is what you actually think it is and then go back and save anything off of your Windows laptop and then replace that O/S with Ubuntu/Dapper.

Good luck.

---

### Post by bodhi.zazen on 2006-11-21
> **dragon-architect said:**
> --Warning-- loooong post --Warning-- (you have been warned)

OK I'll skim to the good parts....

> Then today, I hit across the idea of running a dual-bootable system ... with Windows XP and Ubuntu until I have everything set just the way I need it. Of course, I want to avoid going straight to Ubuntu because I have Windows-only compatible computer games and programs that I have no idea where the individual files necessary for proper operation go.

bulldog had good advice. Run a live CD. If your hardware is recognized, [install](http://www.psychocats.net/ubuntu/installing).

Keep in mind "Linux is not Windows". Your windows games (and other windows software) will likely NOT run on Linux (Ubuntu).

[Linux applications](http://doc.gwos.org/index.php/AppHelper)

It will take some time to learn Linux. While there is nothing wrong with dual booting, it may slow the learning process....

> So, I have one question that maybe a bit n00b-ish, but I'm not what you would call a computer geek:  Would it be possible to share files over a partition boundary in a hard drive?

No problem. [Mount windows partitions](http://www.psychocats.net/ubuntu/mountwindows) See here for [for read-write](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

> The reason I ask this is because this is THE very first time I have thought about partitioning a hard drive, or converting a computer to an OS that did not originally come with it.

Back up your data first, then defragment your windows partition.

Resize and partition away....

> Also, a friend on a chatroom who has very recently switched to Ubuntu has warned me that the Dapper installer is bugged somehow so that it cannot complete the installation, and that Edgy has some pretty nasty bugs. He told me to find a version of Breezy Badger and manually upgrade to Dapper. Is the Dapper installer still bugged, or is what he told me good advice?

This advice is not the best.

Start with Dapper "Live". Sometime the install "hangs" or locks in which case use the "alternate" CD.

Edgy is bleeding edge and you may want to start with Dapper. Bleeding edge = newest, but may have bugs....

I would advise against upgrading from Badger to Dapper for a number of reasons. [list=number][*]I prefer a "fresh install" over an update.[*]The upgrade has a higher chance of failure then a fresh install.[/list] 

> I know it'll be a long and frustrating process switching to a new OS, which is why I'd prefer a dual-bootable system for at least the first few months or however long it takes to get Ubuntu configured to my final preferences.

This is what most do and I think this is a good start.

> At any rate, if I could get some advice pertaining to a recommended version of Ubuntu, I would greatly appreciate it. Please keep in mind I don't have much patience with software, so I'd prefer something with as few bugs as possible.

Phew! What a lungful! *faints*

Dapper for sure.

Best advice I have for you is [READ, READ, READ](http://ubuntuguide.org/wiki/Dapper)

---

### Post by cantormath on 2006-11-21
mac is good linux is better.

---

### Post by dragon-architect on 2006-11-21
wpshooter:

I already hinted that I don't have much money. It'll take almost half of what's in my only savings account to get the parts necessary for building an external backup hard drive. I can't even afford a newer battery for my current laptop to replace the one that won't hold a full charge anymore.

bodhi:

Thanks for all that info. My only real problem with the backing up of all my data is that I'll have to get a spare hard drive first, which will cost money. The premade ones are readily available, but I decided to challenge a magazine article I saw and compared pricing between a commercial external HD and a DIY external HD, and the DIY job came out the cheaper by a slim to respectable margin. Of course, I could burn a bunch of CD's like my dad when he works with his photographs, but I'd prefer a more partable solution.

Cantormath:

hehe. I figured that much. ;P Most of what I've figured from Apple is that it's good with videos and entertainment whilst Windows takes the games market, but Windows isn't stable enough for me.

Dang this is the second attempt at replying. I've had to sit on hold with my mom's ISP to get help about the connection. x.x

---

### Post by irw on 2006-11-29
> **dragon-architect said:**
> My only real problem with the backing up of all my data is that I'll have to get a spare hard drive first, which will cost money.
...
I could burn a bunch of CD's like my dad

One day something will fail in your computer, or you may mess something up, then you will need a backup ... guaranteed. ](*,) 

It will be relatively straightforward to defrag your windows partion, reduce its size, then add additional partitions for data and Linux - but you need to read lots and plan it carefully if this is the first time.  I have never yet lost data to such an exercise:cool:, but many have, and without any form of backup you could be kicking yourself.  I use both CD and an external hard drive for backup, although one would be sufficient.

Even if you were to stick with windows in the end, it is a very good idea to have a seperate partition for your data, then when (not if!) Windows goes belly-up, you are less likely to loose any.

---

