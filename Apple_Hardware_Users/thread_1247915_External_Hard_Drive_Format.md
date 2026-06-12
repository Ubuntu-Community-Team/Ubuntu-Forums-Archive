---
title: "External Hard Drive Format"
date: 2009-08-23
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2009-08-23
Sorry if this is in the wrong forum, but I'm not sure where else it should go. Please feel free to move it if you need to.

I've heard various responses to this question, and have my own preconceived notions about each. I was wondering if I could get some honest input and perhaps resolve some of my incorrect notions.

What is the best external hard drive format (in particular, one which will be interfacing with Mac OS X, Windows Vista AND Ubuntu 9.04)?

FAT32 - This seems to be the fastest, but also seems to be quite unsafe. Not to mention the 4 GB file transfer limit...

NTFS - Most of my externals are this right now. I use NTFS-3G with MacFuse (the unofficial NTFS driver for Mac OS X, which allows writing to NTFS), but file transfer is slow. NTFS is, however, much safer than FAT32.

ext2 - From what I understand, this is fairly compliant with Windows, and somewhat compliant with Mac OS X. I've tried using this, with some success...but not much.

ext3 - Nope. Mac OS X doesn't work well with this, and that's a big problem.

ext4 - What is this? And how well does it work? I just know that Jaunty offered to install using this file system, and it seems to work just fine.

HFS+ - Well...works with Mac of course, sort of works with Ubuntu. No Windows support.

A couple more questions: What file system do you prefer for backup on each system? Is there a preference depending on whether the drive is 3.5" or 2.5"? What color should my external hard drive actually be? Just kidding on the last one :-P

---

### Post by dlmarti on 2009-08-23
According to your needs, I think your locked into Fat32 or NTFS.  I would go with Fat32.

I only use EXT3, but I have no interest in MAC or Windows, they don't run the software I need for my job.
I also don't have the money or time to maintain a MAC or Windows box, just too much trouble.

---

### Post by moore.bryan on 2009-08-23
> **teamjh14 said:**
> 
FAT32 - This seems to be the fastest, but also seems to be quite unsafe. Not to mention the 4 GB file transfer limit...
I've never heard FAT32 is "unsafe;" any rationale for that claim? The problem I have with it is proprietary...
>  NTFS - Most of my externals are this right now. I use NTFS-3G with MacFuse (the unofficial NTFS driver for Mac OS X, which allows writing to NTFS), but file transfer is slow. NTFS is, however, much safer than FAT32.
Same problem here as with FAT32.
>  ext2 - From what I understand, this is fairly compliant with Windows, and somewhat compliant with Mac OS X. I've tried using this, with some success...but not much.
ext2 is antiquated from all I've heard.
>  ext3 - Nope. Mac OS X doesn't work well with this, and that's a big problem.
What do you mean "doesn't work well?" My OS X *Tiger* played well with it...
>  ext4 - What is this? And how well does it work? I just know that Jaunty offered to install using this file system, and it seems to work just fine.
This is just the latest iteration of the ext# file system, with a number of improvements. See [here]("http://ext4.wiki.kernel.org/index.php/Main_Page").
>  HFS+ - Well...works with Mac of course, sort of works with Ubuntu. No Windows support.
And, for what it's worth, I've never heard any positive comments on HFS+.

---

### Post by Tu1J4kXk8NUhMz on 2009-08-23
FAT32 is an old file system, despite still being quite popular. From what I understand, a lot of FAT32's problems arise when being used to hold an operating system. In particular, fragmentation and hard drive errors were a big problem. NTFS was the proper answer to FAT32, implementing several safeguards against issues FAT was prone to. In reading, however, many of these problems seem to be avoidable if they are not a bootable disk. FAT32 is also fairly insecure, even moreso than NTFS.

Drivers for OS X regarding ext2 are unsupported and are no longer updated. That said, they probably worked great on Tiger. Leopard, not so much. ext3 is a journaled ext2, and neither mounts to my desktop anymore with the use of said drivers.

BTW: Thanks for the link to the ext4 improvements. I was wondering.

Mac OS X and Ubuntu are both based on a Unix system, and from my understanding HFS+ is simply Mac's take on ext (or perhaps the other way around). It's an excellent file system, IMO, but really just for OS X.

I guess I *am* kind of stuck with FAT32 or NTFS. Please, any further input would be quite helpful.

I still have hangups with converting to FAT32 due to it's past unreliability. Any input about exFAT would be nice as well

:-D

---

### Post by moore.bryan on 2009-08-24
> **teamjh14 said:**
> FAT32 is an old file system
While I concede this is true, it has proved to be robust enough to still be around; after all, it was first developed in 1976!
> a lot of FAT32's problems arise when being used to hold an operating system. In particular, fragmentation and hard drive errors were a big problem.
This would make sense, but I don't think you're installing an os on the drive; therefore, these concerns are minor if they exist at all.
> NTFS was the proper answer to FAT32, implementing several safeguards against issues FAT was prone to. In reading, however, many of these problems seem to be avoidable if they are not a bootable disk. FAT32 is also fairly insecure, even moreso than NTFS.
Once again, what's "insecure" about FAT32? It's true NTFS can easily be encrypted, but there are a number of tools you can use to secure your FAT32 data. Or, are you talking about the possible loss of data?
>  Drivers for OS X regarding ext2 are unsupported and are no longer updated. That said, they probably worked great on Tiger. Leopard, not so much.
That makes sense. I found Mac OS X so poorly designed I dumped it for a Debian 5.0/XFCE 4.62 mix.
> ext3 is a journaled ext2, and neither mounts to my desktop anymore with the use of said drivers.
Hmm... that strikes me as strange.
> BTW: Thanks for the link to the ext4 improvements. I was wondering.
No worries.
> 
Mac OS X and Ubuntu are both based on a Unix system, and from my understanding HFS+ is simply Mac's take on ext (or perhaps the other way around). It's an excellent file system, IMO, but really just for OS X.
Most of what I've read about the original hierarchical file system is that it was based more on Apple's sophisticated operating system (SOS) than ext and was trying to "keep-up" with Microsoft's disk operating system (DOS). Like I wrote above, I found HFS+ slow and unresponsive for me, but that may have been caused by my, somewhat, antiquated iMac G4 "Flowerpot." :-)
>  I guess I *am* kind of stuck with FAT32 or NTFS. Please, any further input would be quite helpful.
[quote] I still have hangups with converting to FAT32 due to it's past unreliability. Any input about exFAT would be nice as well
I've only ever used FAT32 on my external hard drives (one Western Digital 100GB, one Western Digital 250GB, and one LACIE 250GB) and the hard drives' disks died long before FAT32 caused any issues. Since I first went to Linux back in 2006, NTFS support has come a long way; however, strong fears die hard. Frankly, NTFS support *sucked* when I first "converted," but now is very strong. exFAT would cause the same proprietary pauses as FAT32 and NTFS, but I think your number one concern seems to be viability with your Mac.

---

### Post by cascade9 on 2009-08-24
FAT32- Ancient, came out on win95OSR2.1 IIRC. I've seen more than my share of FAT problems, not something I would use unless it was for a short-term solution. 

NTFS- The only real choice for a NT (not 9x) based windows system. 

EXT2- Also pretty old, not something you would use for a native filesystem on a linux hdd these days. For max compatability with MacOS and Windows systems its not that bad a choice

EXT3- Newer, probably the best stuffing around to performance ratio with Windows. If you have had issues with EXT2/EXT3 support on Mac, tried EXT2FSK? 

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) 

BTW, EXT3 will probably mount as EXT2 under Windows or Mac, depending on how much poking you want to do. 

EXT4- Too new IMO. It should work with Windows and Mac, but really not worth the effort. 

HFS+ - Actually does have Windows support, but no being a mac user I've never had to try any of the 'solutions' for HFS+ with Win 

[http://www.macwindows.com/disks2.html](http://www.macwindows.com/disks2.html)

> **teamjh14 said:**
> What is the best external hard drive format (in particular, one which will be interfacing with Mac OS X, Windows Vista AND Ubuntu 9.04)?

Depends. If they are all your machines, or machines you have good access to, I would go for EXT2/3.  If your going to be trying to hook up to 'strange' MacOS or Win machines...err...probably NTFS. *washes mouth out with soap after suggesting that* 

> **teamjh14 said:**
> A couple more questions: What file system do you prefer for backup on each system? Is there a preference depending on whether the drive is 3.5" or 2.5"? What color should my external hard drive actually be? Just kidding on the last one :-P

Heh, my 'backup' normally consists of 'buy new hdd, copy over data to new partition, remove old drive, put in anti-static bag and lock that into storage" or "get old hdd out of storage, copy over data, put back into storage" LOL. So it tends to be whatever file system I was running last. 3.5'' drives are faster, and generally cheaper. 2.5'' drives are more of  a handy 'pocket' size, and if your using them from USB, they normally dont need a powerbrick. 

You drive should be red, it will go faster :P

---

### Post by Tu1J4kXk8NUhMz on 2009-08-24
> **moore.bryan said:**
> Once again, what's "insecure" about FAT32? It's true NTFS can easily be encrypted, but there are a number of tools you can use to secure your FAT32 data. Or, are you talking about the possible loss of data?

You hit the nail on the head. FAT32 could not be encrypted. Apparently that was the info I was fishing for, as I'd like to know if there is any FAT encrypting software out there. Loss of data was a big problem as well at one point. I'm not familiar with FAT capabilities now (or software that provides new capability using FAT), so if you could point me in the right direction that would be awesome!

> **moore.bryan said:**
> Hmm... that strikes me as strange.

With OS X moving more towards Intel compatibility (Snow Leopard is a "Mactel" exclusive), changes have been made in the OS X structure that have rendered mounting ext2/3/4 improbable. Don't ask me why, as I don't know exactly what's changed that has made this so difficult, but with no work being done on the drivers (as far as I know), this is probably not possible...

> **moore.bryan said:**
> Most of what I've read about the original hierarchical file system is that it was based more on Apple's sophisticated operating system (SOS) than ext and was trying to "keep-up" with Microsoft's disk operating system (DOS). Like I wrote above, I found HFS+ slow and unresponsive for me, but that may have been caused by my, somewhat, antiquated iMac G4

My apologies, I misspoke. The original HFS was originally intended for removable media (floppies, CDs, tapes I think) but was adapted into HFS+ to support the OS. HFS+ (the plus means extended, actually), among other adjustments, added a journaling system. The file system probably continues to change as OS X does, meaning backwards compatibility has probably bitten the dust gradually.

> **moore.bryan said:**
> I've only ever used FAT32 on my external hard drives (one Western Digital 100GB, one Western Digital 250GB, and one LACIE 250GB) and the hard drives' disks died long before FAT32 caused any issues. Since I first went to Linux back in 2006, NTFS support has come a long way; however, strong fears die hard. Frankly, NTFS support *sucked* when I first "converted," but now is very strong. exFAT would cause the same proprietary pauses as FAT32 and NTFS, but I think your number one concern seems to be viability with your Mac.

I was hoping to hear this. Back in the day, FAT wasn't preferred for much. So I guess I just wanted to know there wasn't a strong contingent out there telling me "What the hell are you doing?!?"

> **cascade9 said:**
> FAT32- Ancient, came out on win95OSR2.1 IIRC. I've seen more than my share of FAT problems, not something I would use unless it was for a short-term solution. 

Can you explain some of the issues you've had with FAT, and also what OSes you've seen problems in? Most flash drives and USB micro drives are formatted in FAT32, so I wonder if you consider this a problem.

> **cascade9 said:**
> EXT2- Also pretty old, not something you would use for a native filesystem on a linux hdd these days. For max compatability with MacOS and Windows systems its not that bad a choice

EXT3- Newer, probably the best stuffing around to performance ratio with Windows. If you have had issues with EXT2/EXT3 support on Mac, tried EXT2FSK?

I have, in fact. The last release of OS X had no problem using the EXT driver. There were, however, loads of problems with R/W between the Ubuntu drive and Mac OS X. With the latest release (Leopard) of OS X, it doesn't even try to mount it. Unfortunately, this ext2 driver haven't been updated since 12/2006, and don't look to be again anytime soon.


> **cascade9 said:**
> HFS+ - Actually does have Windows support, but no being a mac user I've never had to try any of the 'solutions' for HFS+ with Win 

This is interesting. I've never seen this before. I'll really have to look into this, as I think that it would be useful for inter-partition work, if nothing else.

> **cascade9 said:**
> Depends. If they are all your machines, or machines you have good access to, I would go for EXT2/3.  If your going to be trying to hook up to 'strange' MacOS or Win machines...err...probably NTFS. *washes mouth out with soap after suggesting that* 

My biggest concern is if I ever try to take one of my drives and hook it up to an older Macintosh or something (I do a lot of work on a college campus, and some of the Macs are quite outdated). I suppose in that scenario, though, I ought to just bring a FAT drive and transfer the info later to wherever it should be.

> **cascade9 said:**
> Heh, my 'backup' normally consists of 'buy new hdd, copy over data to new partition, remove old drive, put in anti-static bag and lock that into storage" or "get old hdd out of storage, copy over data, put back into storage" LOL. So it tends to be whatever file system I was running last. 3.5'' drives are faster, and generally cheaper. 2.5'' drives are more of  a handy 'pocket' size, and if your using them from USB, they normally dont need a powerbrick. 

Ha ha! That's been my solution for years. In fact, in my younger days I just assumed anything I did on a computer was expendable. However, I'm a graphic designer now, and the more my portfolio grows, the more I need to backup.

Powerbricks are unappealing, as I have two 3.5" drives which use up a good portion of my power strip as it is. Now that I think about that, those two might be more effective for back ups, and using my 2.5" might make better extensions for my existing internal hard drive.

> **cascade9 said:**
> You drive should be red, it will go faster :P

Noted. I have flame stickers on order from Amazon.:)

---

### Post by moore.bryan on 2009-08-25
> **teamjh14 said:**
> I'm not familiar with FAT capabilities now (or software that provides new capability using FAT), so if you could point me in the right direction that would be awesome!
I know TrueCrypt can do FAT32. From the TrueCrypt website:
> **Is it possible to change the file system of an encrypted volume?**       Yes, when mounted, TrueCrypt volumes can be formatted as FAT12, FAT16,          FAT32, NTFS, or any other file system. TrueCrypt volumes behave as standard          disk devices so you can right-click the device icon (for example in the '*Computer*' or '*My Computer*' list) and select '*Format*'. The actual volume contents will be lost. However, the whole volume will remain encrypted. If you format a TrueCrypt-encrypted partition when the TrueCrypt volume that the partition hosts is not mounted, then the volume will be destroyed, and the partition will not be encrypted anymore (it will be empty).

---

### Post by cascade9 on 2009-08-26
> **teamjh14 said:**
> Can you explain some of the issues you've had with FAT, and also what OSes you've seen problems in? Most flash drives and USB micro drives are formatted in FAT32, so I wonder if you consider this a problem.

Noted. I have flame stickers on order from Amazon.:)

Mainly Win9x (all flavours) and Win2K/XP. Corruption issues, data loss, etc. Its not that common, I mainly have seen it on other peoples PCs that they want me to fix, but I am stil pissed about osing my original hdd contents from FAT32 doing something. Tried all ort of tools, but the data was gone, forever. I'm probably harder on FAT32 than it diserves because of that. ;) 

I havent had any problems with flash drives doing that, and I dont consider flash drives in FAT32 to be an issue. But IMO, flash drives exist to move data from one hdd to another mianly (yes, you can run an OS of a flash drive, but then it should be in some other file system). 

BTW- was the drives you were having issues with on MacOSX with the EXT driver EXT2 or EXT3? It might be worth a try on EXT2 if you were using EXT3, as I'm pretty sure it was only made for EXT2 and EXT3 reading/writing is from the EXT2/3 compatibility, not from driver support. Thats just a thin 'maybe' though.

Flame stickers! Woohooo! It will be as fast as 4 x SATA2 7200 drives in RAID then :D

---

### Post by Tu1J4kXk8NUhMz on 2009-08-27
> **cascade9 said:**
> 
BTW- was the drives you were having issues with on MacOSX with the EXT driver EXT2 or EXT3? It might be worth a try on EXT2 if you were using EXT3, as I'm pretty sure it was only made for EXT2 and EXT3 reading/writing is from the EXT2/3 compatibility, not from driver support. Thats just a thin 'maybe' though.

Flame stickers! Woohooo! It will be as fast as 4 x SATA2 7200 drives in RAID then :D

Ext2, believe it or not. The volume containing Ubuntu was formatted ext2 specifically so I could use the driver. Then Leopard came out. In fact, I think it was one of the updates the screwed the driver. Technically, ext3 DID have read/write capability using the driver. But, it was a terrible idea, as it wasn't uncommon to cause a OS X kernel crash. I know from experience, of course, because I am thick-headed. :P

Ironically, a friend of mine just bought a portable hard drive. Guess what he put on it?

---

