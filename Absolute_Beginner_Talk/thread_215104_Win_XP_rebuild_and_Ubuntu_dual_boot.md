---
title: "Win XP rebuild and Ubuntu dual boot"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by jason7655 on 2006-07-13
Hello everyone.
I've successfully installed Ubuntu on an old box but since I don't have a KVM it has received little attention.

I'm now looking at rebuilding my personal box and I need some advice.

I have to have win xp on there so that's not the question.

Let's say I have a 120 gig hard drive.

I want windows on it's on partition, and its file system on its on partition.  I guess I would want a partition or 2 for Ubuntu and it's file system (these would be much smaller since I'm experimenting).

What would be my ideal partition sizes?  I have seen some guides out there for dual boot between xp and ubuntu, even one video that shows it.  What's the swap partition for?

I know I'm all over the place with questions, but hopefully someone will be able to respond.

---

### Post by indytim on 2006-07-13
Jason,

How you divide up your HD really depends on what the inteded purposes are.  Here's how I cut up my HD for dual-boot Win2kPro and Dapper Gnome:

Windows NFTS 10g
Linux  EXT3 15g
Swap .5g
Windows Servers NTFS 2g
Share 1 1.2g FAT32
/home Ext3 5g
Media Share FAT32 110g

I did all of the partioning before I did the install of Linux.  Purposely made the partitions different sized to avoid doing the "incredible deed".

Hope this helps and good luck with your upcoming Ubuntu activites.

IndyTim

---

### Post by wombat20 on 2006-07-13
It's best to install Windows first if you want to dual boot.  Windows doesn't play nicely with other OS's, so would wipe the bootloader/Master Boot Record.

You could partition the disk first, but I'm not sure this is really necessary.  I think Ubuntu (or at least GParted) can resize an existing partition ok - but hopefully someone will confirm that.

How big?  Decide how much space you really need for Windows - is it mostly for games, or just a single app?  

When Ubuntu installs, it's best to let it decide for itself how big the swap partition should be and all that.

---

### Post by jason7655 on 2006-07-13
Well, on that note here's another question.

Win xp and Ubuntu cannot share files....right?

I'm assuming that it can't, so 2 seperate file systems would have to exist.

The Ubuntu side of things would be more for experimenting and playing around with while the XP will be used to do the things I've been doing.

---

### Post by wombat20 on 2006-07-13
You can access your windows drives from Ubuntu (should be automatic).  With some fiddling around (download a windows prog) you can access Linux partitions from WinXP too.

But if you're thinking about sharing your Thunderbird user files so whichever one you use you have the same messages, account etc, forget it.  They work slightly differently.

---

### Post by bigken on 2006-07-13
hi this how i have a 120 gig hdd 
10 gig winxp 
10 gig ubuntu root /
swap twice your ram (ie 512=1024)
ubuntu home 30 gig 
the rest fat 32 
point of thumb  swap should always be 2 times your ram ;)
install winxp 1st

---

### Post by BigDave708 on 2006-07-13
> **wombat20 said:**
> It's best to install Windows first if you want to dual boot.  Windows doesn't play nicely with other OS's, so would wipe the bootloader/Master Boot Record.

You could partition the disk first, but I'm not sure this is really necessary.  I think Ubuntu (or at least GParted) can resize an existing partition ok - but hopefully someone will confirm that.

It would make sense to partition the hard drive before installing XP. If you let XP install on the one partition on your hard drive, and then tried to resize that partition to make room for the other Ubuntu partitions, it would take ages to do because when you installed XP it would sprawl itself out over the entire drive, and the files towards the end of the disk would have to be deleted and re-written closer to the start of the disk.

> **jason7655 said:**
> Win xp and Ubuntu cannot share files....right?

Nope, they can. Ubuntu can, however, only read from and write to FAT32 partitions. Ubuntu can see NTFS partitions and usually open the files on them, but cannot write to them. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=212995]("http://www.ubuntuforums.org/showthread.php?t=212995")

There are several freeware applications on the net that can be installed in Windows XP and they can read ext3 file systems, the file system that Ubuntu uses. I can't actually remember the name of that program at the moment though ](*,) . . . can anyone help me out there? :mrgreen:

---

### Post by jason7655 on 2006-07-13
(THIS POST WAS MADE BEFORE THE POST RIGHT ABOVE)
so from inside of linux I can open a .jpg, .html, .mp3, etc that is located on the windows partition?  Can windows applications and linux operations co-exist on the same partition and operate w/o a problem?

So looking at what was said earlier:
"Windows NFTS 10g
Linux EXT3 15g
Swap .5g
Windows Servers NTFS 2g
Share 1 1.2g FAT32
/home Ext3 5g
Media Share FAT32 110g"

Can you go into why you did it this way?

I mean, I could see myself doing
WinXP 20G
Linux 10G
Swap .5G (not sure why I have swap?)
Files Partition (the rest G)

---

### Post by BigDave708 on 2006-07-13
> **jason7655 said:**
> so from inside of linux I can open a .jpg, .html, .mp3, etc that is located on the windows partition?  Can windows applications and linux operations co-exist on the same partition and operate w/o a problem?

Yep, you can access those sorts of files from your XP partition in Ubuntu. I wouldn't advise trying to install both Windows applications and Ubuntu on the same partition though - that could get messy . . .

---

### Post by crystal on 2006-07-13
> But if you're thinking about sharing your Thunderbird user files so whichever one you use you have the same messages, account etc, forget it. They work slightly differently.
No, it can be done. I have done it with a shared Ext3 partition, another person did it with a shared FAT32 partition.
[ Howto: Share Thunderbird & Firefox data between Ubuntu & Windows](http://ubuntuforums.org/showthread.php?t=203524)

> There are several freeware applications on the net that can be installed in Windows XP and they can read ext3 file systems, the file system that Ubuntu uses. I can't actually remember the name of that program at the moment though
I use the one from [fs-driver.org](http://fs-driver.org).

---

### Post by coffeecat on 2006-07-13
> **BigDave708 said:**
> There are several freeware applications on the net that can be installed in Windows XP and they can read ext3 file systems, the file system that Ubuntu uses. I can't actually remember the name of that program at the moment though ](*,) . . . can anyone help me out there? :mrgreen:

You'll find ExtIFS for Windows (copes with ext3 as well) here:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It's excellent. I use it myself.

**jason7655**, You say you just want to experiment and play with Ubuntu at first. I guess you want to make it simple. Here's a couple of suggestions:

Apart from Windows on a ntfs partition, you only need either two or three as follows for a straightforward setup:

1 ext3 partition for Ubuntu root. Don't bother with a separate /home or /boot partition.

2 Swap partition - as someone else has said, make that 2x your RAM.

3 Optional - fat32 partition which can be read and written to by both Windows and Ubuntu, for shared files.

Or, even simpler, if you don't want the shared fat32 partition - Create a ntfs partition for Windows and leave, say, 10-20GB as unallocated space on the hd. When you install Ubuntu, point the installer at the unallocated space and let it get on with it. That's what I used to do when I first started with Linux. Never failed. Setting up custom partitions is for when you have more experience and you know what you need them for.

---

### Post by jason7655 on 2006-07-13
thanks for the speedy response everyone.  Very helpful stuff.

---

### Post by BigDave708 on 2006-07-13
> **crystal said:**
> I use the one from [fs-driver.org](http://fs-driver.org).

> **coffeecat said:**
> You'll find ExtIFS for Windows (copes with ext3 as well) here:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It's excellent. I use it myself.

That's the one! Thanks :mrgreen:

---

### Post by bigken on 2006-07-13
Hi I think the reason for a swap partion works the same as windows virtual memory ie when your  ram resourse  get low it uses the hdd swap partion I could be wrong :rolleyes:

---

### Post by italianboy on 2006-07-13
Hi, 
i've installed two OS(Ubuntu and XP) on differrent partitions. Later i decided to have Linux on another PC, so i deleted the whole partition (using PartitionMagic) and merged it with another one. Now when i try to boot my PC - i get an error message: GRUB Error 17 and something about stage 1.5. What can i do?
P.S. Excuse me for my English.

---

### Post by shinji257 on 2006-07-13
If you have only Windows XP on that drive now then boot from your XP install disc and start the Recovery Console.  From there run FIXMBR and FIXBOOT and that will reload the normal XP boot loader.

---

### Post by coffeecat on 2006-07-13
> **italianboy said:**
> Hi, 
i've installed two OS(Ubuntu and XP) on differrent partitions. Later i decided to have Linux on another PC, so i deleted the whole partition (using PartitionMagic) and merged it with another one. Now when i try to boot my PC - i get an error message: GRUB Error 17 and something about stage 1.5. What can i do?
P.S. Excuse me for my English.

This is from the Grub manual (errors returned by stage 1.5):

> 17 : Cannot mount selected partition.
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.Grub is the bootloader used by Linux. Whatever you did with Partition Magic has created a partition that Grub cannot recognise.

I'm not quite sure what you are trying to do. The PC with the error message - are you trying to restore that to a single boot Windows setup, or do you just want Linux on it? If you want just Windows do what shinji257 said. If Linux - we need some more details to suggest what to do.

---

### Post by italianboy on 2006-07-14
Thanks for the help

---

### Post by jason7655 on 2006-07-14
ok...so i'm hoping someone is on that can help tonight.

I'm sitting here in front of my windows machine.  I have installed windows on the first 12g.

The swap that is mentioned...that isn't formated in windows with a file system right?

Are you guys referring to linux swap?

---

### Post by BigDave708 on 2006-07-14
> **jason7655 said:**
> ok...so i'm hoping someone is on that can help tonight.

I'm sitting here in front of my windows machine.  I have installed windows on the first 12g.

The swap that is mentioned...that isn't formated in windows with a file system right?

Are you guys referring to linux swap?

The /swap partition is the one that is meant to be twice the size of your RAM. It's used by Linux as the equivalent of the paging file in Windows. It's basically a sort of overflow storage where Linux stores the data that it wants to store on your RAM but there is not enough room.

---

### Post by jason7655 on 2006-07-14
ok...so probably the best thing to do now is:

I have my 102 gigs left.

Prob just partition 90 gigs for storage, apps, whatever.

Then the last 12 can go for Ubuntu, and just let it fend for itself on the remaining 12...since I'm not sure I know how to do that whole swap thing.

That might be the easiest thing to do.

---

### Post by BigDave708 on 2006-07-14
> **jason7655 said:**
> Prob just partition 90 gigs for storage, apps, whatever.

Then the last 12 can go for Ubuntu, and just let it fend for itself on the remaining 12.

Most applications you install in Ubuntu will go into the main Ubuntu partition (the one you say is 12GB), and not into the main 90GB partition. However, 12GB should still be large enough for Ubuntu and all the applications you should really ever need.

---

### Post by jason7655 on 2006-07-14
now win xp isn't giving me the option of formating that drive as ntfs (edit...this should be fat32) since i'm in win xp now

---

### Post by bigken on 2006-07-17
use qtparted to create your partions 1st theres a live disc you can download and burn theres a link somewere on this forum ;)

---

