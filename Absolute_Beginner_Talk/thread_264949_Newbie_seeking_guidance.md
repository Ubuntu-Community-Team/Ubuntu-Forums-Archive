---
title: "Newbie seeking guidance"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by mo79 on 2006-09-25
I have a Dell Dimension 4550 (512MB RAM, 60GB HD) with, you guessed it, Win XP Home and after a little tinker with the LiveCD (incidentally everything was detected but my scanner, a UMAX AstraSlim SE has some issue?) I want to have Ubuntu dual boot with my WinXP.

I'm pretty good with Windows, but know that means squat on Linux. So what's the best way to partition and install etc.?
I understand to make backups but I'd really appreciate it if this can be done as painlessly as possible as this is the only comp I have, and as someone who works with music composition programs I really don't want Windows and all that to vanish. I'm currently using 16GB of 60GB.

I think I have a backup partition and could delete that as I have a retore CD?
I know this has been talked about elsewhere, but I'm a bit nervous when doing stuff like this so would appreciate a personal response. Thanks.

---

### Post by CatKiller on 2006-09-25
I think that the "restore cd" actually only copies stuff from the backup partition, so only delete that if you don't want to restore.

Given that you've mentioned music composition, I'd be tempted to not touch that drive and install Ubuntu on a different one. 24 channels of 24bit/48kHz WAV files (that I work with) sucks up space pretty quickly. If you put in a second drive, you can have the whole of that 60GB for Windows, and as much as you buy/borrow for Ubuntu.

As an alternative, there are many guides - and an installer default - for resizing the existing Windows partition and installing Ubuntu into the newly-made space. It'll be quicker if you defragment that partition in Windows first, and make sure that you only **resize** the partition, not delete.

Welcome to the Ubuntu forum!

---

### Post by TeeAhr1 on 2006-09-25
Here is the [guide]("http://users.bigpond.net.au/hermanzone/") that I used when I first installed Ubuntu.  It's a very concise guide, I'd recommend it to anyone who's doing this for the first time.

My advice, for what it's worth: Read it first!!!!11!  Then print it out, and have it with you while you install.  But go through it first, I assure you the middle of the installation is a bad time to discover that you're not sure what you're doing.  Of course, if you have any questions or need assistance, we're a click away.  Good luck, have fun, and welcome!

---

### Post by GoneWithTheWind on 2006-09-25
The regular install kept locking up and didn't work for me.

Then I downloaded the gparted and alternate install live CD's and these worked very well.

Also it helps to run defrag a few times, like 20 times or so, before resizing the partitions.

---

### Post by mo79 on 2006-09-25
Brilliant. :) I might just consider a second HD - although having been used to Windows since 3.11 it's often a habit of mine to have unused projects removed/backed straight to CD.

Is the Dapper partitioner safe or should I get SystemRescueCD?...Not sure what's safer/better.

Thanks for the replies - means a lot!

---

### Post by latecomer on 2006-09-25
Download Gparted Livecd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Have a look at these [http://www.linux.com/article.pl?sid=06/07/20/1654251](http://www.linux.com/article.pl?sid=06/07/20/1654251)
Like John Rupp said, defrag several times before you start.
One last thing: you might want to disable XP's pagefile and then defrag a couple of times; my XP's pagefile was in the middle of empty space on my HD and couldn't be moved by defragging (it shows up as a green band on volume info screen in XP's defragger) you can enable it again afterwards.
Hope it works out well.

---

### Post by mo79 on 2006-09-25
Wonderful! One other thing for now, if I installed a second HD just for Ubuntu what's the installation procedure for that? And if possible can XP still be the default booting OS? For the time being Ubuntu will be a hobby thing.

Cheers again.

---

### Post by gn2 on 2006-09-25
The simplest easiest way to achieve what you want is to install a second hard drive and install Ubuntu on that.
Once the second hard drive is fixed in place, disconnect the power connector to the Windows hard drive.
Now you can safely install Ubuntu from the live CD onto the second hard drive without the Grub bootloader being written over the Master Boot Record of the Windows drive.
Once install is complete, you can re-connect the power to the Windows hard drive, and select the boot device from the bios by pressing F8 and choosing the boot device.(or other key depending on model)

Remember: Do not plug/unplug IDE SATA or power cables unless the PC is switched off, or you'll get an expensive flash of light.....

There are many more detailed guides on this kind of thing, suggest you do some Googling...

Good Luck

---

### Post by CatKiller on 2006-09-25
As an addendum to what gn2 said, in my BIOS setup I have an option - called Boot Sprite or something similar - that means that I get a choice of which drive to boot from without having to go into the BIOS each time, and without having either the Windows boot thing or grub affacting the other drive in any way. You might have something similar.

---

### Post by mo79 on 2006-09-25
Was just looking at my BIOS and indeed saw an option that allows me to choose what order drives are looked at first to boot. The option from gn2 sounds my cup of tea perfectly!

If I install to a second hard drive with my initial HD unplugged, I assume it will be assigned C:, but that won't interfere with my Windows being C: I'm guessing?...

I'd also like to install from my second CD drive as my first one's a bit rough with discs somehow, yet I can't seem to see an option to get this - I only see my HD, floppy and first CD(DVD) drive in the boot list. I have Dell BIOS A04.

Thanks for your patience. Only earlier today I was thinking of not getting involved with Ubuntu but the advice I'm getting is very comforting.

One other thing, can my UMAX AstraSlim SE work with Ubuntu by tweaking?...I guess I'll learn once it's installed. ;)

---

### Post by confused57 on 2006-09-25
Maybe this guide can help:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

I also have a Dell Dimension 4550.

---

### Post by CatKiller on 2006-09-25
> **mo79 said:**
> If I install to a second hard drive with my initial HD unplugged, I assume it will be assigned C:, but that won't interfere with my Windows being C: I'm guessing?...

Linux doesn't work in drive letters like that. You've got the fun of getting your head round the Linux filesystem and mount points and the like to come, I guess. It's really straightforward, though, just different.

But yes, the partition that Windows calls C: will continue to be called C: by Windows when you boot from it, even if that drive is now actually the Primary Slave. At least, it always has in my (admittedly limited) experience.

> I'd also like to install from my second CD drive as my first one's a bit rough with discs somehow, yet I can't seem to see an option to get this - I only see my HD, floppy and first CD(DVD) drive in the boot list. I have Dell BIOS A04.

If it comes to it, and your motherboard will only boot from the first CD drive, you could always swap the drives over. After all, you'll already have the case open to install the second hard drive. But even though my BIOS screen only has CDROM as the boot order option, it does still try to boot from each of them in turn.

> Thanks for your patience. Only earlier today I was thinking of not getting involved with Ubuntu but the advice I'm getting is very comforting.

With this many people, there's got to be **someone** who knows about pretty much anything you could want to know about. I'm pleased that you're finding us (not necessarily me, mind) helpful. Won't be long before you're helping people too.

---

### Post by gn2 on 2006-09-26
> **mo79 said:**
> 
If I install to a second hard drive with my initial HD unplugged, I assume it will be assigned C:, but that won't interfere with my Windows being C: I'm guessing?...

I'd also like to install from my second CD drive as my first one's a bit rough with discs somehow, yet I can't seem to see an option to get this - I only see my HD, floppy and first CD(DVD) drive in the boot list. 

The BIOS option to boot from CD is not usually drive specific, it will detect and attempt to boot from any disc found in either drive.

When you install Ubuntu on a second hard drive as slave  with the Windows drive (still set as master) unpowered, Ubuntu will not know Windows drive is there, so will not assign it a drive letter(s)

This solution effectively gives two independent computers in one box.
If you don't configure Ubuntu to mount and read from the Windows drive it will never know it's there.
If you want to protect your Windows installation, this is a *very* good thing.

---

### Post by mo79 on 2006-09-26
Excellent, I have a very clear picture of what I want to do now - I even found out that the SANE thing supports my scanner; not a big deal but still good.
No doubt I'll be back when I actually go through with the procedure lol.

Thanks to all here - the support is equal (no, perhaps better) than from Microsoft people.

---

### Post by mo79 on 2006-09-26
One small thing. If I didn't select from the BIOS which drive to boot from will it automatically boot the primary, WinXP drive by default? (which I'd quite like, at least initially).

---

### Post by gn2 on 2006-09-26
It will boot in the order listed in the BIOS.

Just choose which hard drive you want to boot from by default and make sure it is set before the other one.

You will only have to press F8 to select the non-default drive.

---

### Post by mo79 on 2006-09-26
Perfect. ;)

Now to get me a hard drive. I see quite cheap 80GB hard drives for about £30...What's the lowest size hard drive I should get for Ubuntu on it's own?
Some 30/20GB spares on eBay for about a tenner seem tempting...

---

### Post by gn2 on 2006-09-27
This would do nicely.
[http://www.ebuyer.com/UK/product/34419](http://www.ebuyer.com/UK/product/34419)

Or PCworld have a mad policy where you can order on-line and collect at the store with large discounts...
Samsung and Hitachi drives run quietly, but that's a thing of mine, hate PC noise and all components I buy have to  be quiet ones...
[http://www.silentpcreview.com/](http://www.silentpcreview.com/)

Trouble with second hand drives on ebay is they don't always represent good value per Gb... and are usually older slower and noisier.

I have been lucky on eBay a few times, and have a selection of good 2.5" drives sourced there.

I see you're in London, you should be spoiled for choice with PC shops flogging stuff at good prices... That way if there's a problem you can take it back and get a replacement easily.

Choices choices.

WARNING: Once you open that case and start tinkering there's no going back, it can be dangerously addictive upgrading modifying and fiddling about....

---

### Post by xpod on 2006-09-27
> I see you're in London, you should be spoiled for choice with PC shops flogging stuff at good prices... That way if there's a problem you can take it back and get a replacement easily.

Choices choices.

WARNING: Once you open that case and start tinkering there's no going back, it can be dangerously addictive upgrading modifying and fiddling about....
Reply With Quote 

I second my compatriots opinion there:D 
Londons a bit like the "WWW".....Theres just soooo much to chose from.
(i`d still rather be up princess street)

I opened my pc`s up a couple of days after i got them and it`s the best therapy i could have had.....

Enjoy....opening the pc up that is(london am no sae sure aboot:D )

---

### Post by mo79 on 2006-09-27
I've only opened my comp a few times before - I know what I'm doing, but I still think "is this right?" a lot lol.

Will prob get either [http://www.misco.co.uk/productinformation/~100001~/Excelstor%203.5%20%20Hard%20Drive%2080GB%207200rpm%202MB%20Buffer%20ATA-133.htm#](http://www.misco.co.uk/productinformation/~100001~/Excelstor%203.5%20%20Hard%20Drive%2080GB%207200rpm%202MB%20Buffer%20ATA-133.htm#)
or
[http://www.ebuyer.com/customer/products/index.html?rb=21911006049&action=c2hvd19wcm9kdWN0X3Jldmlld3M=&product_uid=97632](http://www.ebuyer.com/customer/products/index.html?rb=21911006049&action=c2hvd19wcm9kdWN0X3Jldmlld3M=&product_uid=97632)  in the next day or so.

Online shops are still better than most stores I know here, in terms of price. I saw an Ununtu book for about £30 at PC World, half that price is on Amazon...but better off freeloading from the forum as I go. ;)

---

### Post by gn2 on 2006-09-27
Everyone has their own hardware preferences, it can be highly emotive, but I would counsel against the Exelstor drive.

Go for the Ebuyer Seagate one on the basis of the 5 year warranty, and I've always had good aftercare from ebuyer.

---

### Post by xpod on 2006-09-27
Thats what i stuck in here,a smaller 40g seagate.
Used to have xp on it and ubu on some tiny wee thing i stuck in as well....
Im all better now and there`s no slave and no xp;)

---

### Post by mo79 on 2006-09-28
Cool, I'm going for the Seagate then. Was initially looking at 40GB drives, but 80GB ones are strangely the same price so might as well go for that.
Just out of interest - not that it bothers me much - if I wanted to give half the new drive's space for Windows file use could I just do that in the Ubuntu installer? i.e. create 40GB NTFS and then would Windows see that as a 40GB drive?
Doesn't bother me too much as I'm very conservative with disk space anyway, and maybe some day I'll only have one Windowless, master drive. ;)

---

### Post by CatKiller on 2006-09-28
> **mo79 said:**
> Just out of interest - not that it bothers me much - if I wanted to give half the new drive's space for Windows file use could I just do that in the Ubuntu installer? i.e. create 40GB NTFS and then would Windows see that as a 40GB drive?


You'd be better off with a 40GB FAT32 partition - then Windows and Ubuntu can both use it easily.

---

### Post by xpod on 2006-09-28
The way i did it when i was dualbooting was to use fdisk(no xp cd) to first create the windows partition which i gave about a third of it to..
You should just be able to use your xp cd to use however much you want....I think?

THEN once that was all done i used either the installer on the ubu cd and just pointed it towards the unallocated space and let it do the rest automatically...OR i have used the Gparted live cd itself to first create the  required partitions then chose the "create partitions manually" option on the ubunto live cd once it gets to that stage....

---

### Post by mo79 on 2006-09-28
Ah cool, so it would be wise/necessary to have, say a FAT32 partition at the beginning of the drive and the Linux stuff at the end?

I currently have 512 RAM but dead certain that I'm going to double it by the end of the year, so should I make my Linux swap 1535MB in advance?
And in general if I upgraded, say my DVD drive or any other hardware, would Ubuntu autodetect the new hardware (if it can)?

My head's getting used to this ;)

---

### Post by CatKiller on 2006-09-28
> **mo79 said:**
> Ah cool, so it would be wise/necessary to have, say a FAT32 partition at the beginning of the drive and the Linux stuff at the end?

Not necessarily. It depends what you're planning on doing with it. If you're going to boot Windows off that drive as well, then I think Windows copes better if its booting off the first Primary partition. If you're only going to boot Linux off that drive, then you might as well put your EXT3 partition at the beginning and stick a FAT32 partition at the end. If it's just for data, neither Linux nor Windows really care where it is.

> I currently have 512 RAM but dead certain that I'm going to double it by the end of the year, so should I make my Linux swap 1535MB in advance?
And in general if I upgraded, say my DVD drive or any other hardware, would Ubuntu autodetect the new hardware (if it can)?

I really have no idea ;) I suppose you might as well have the swap partition larger, since you're partitioning now, and won't want to later. I made mine 1 Gig while I was partitioning for the same reason. I don't think it particularly matters if the swap partition is bigger than you need, but I seem to remember reading somewhere that swap bigger than 2 Gigs is not a good idea.

---

### Post by mo79 on 2006-09-28
Brilliant, and yeah I want the new drive as half Ubuntu, half FAT32.

The only thing I can think of right now - to keep being a pest hehe - is HD jumper settings, I want Windows as my main thing so will I keep that on master, or during the Ubuntu install, when it's disconnected, is the new drive temporarily master or still slave?..

---

### Post by gn2 on 2006-09-28
> **mo79 said:**
> Brilliant, and yeah I want the new drive as half Ubuntu, half FAT32.

The only thing I can think of right now - to keep being a pest hehe - is HD jumper settings, I want Windows as my main thing so will I keep that on master, or during the Ubuntu install, when it's disconnected, is the new drive temporarily master or still slave?..

Leave the Windows where it is, put second drive on slave connector and set jumper to slave or cable select.

You can install Ubuntu and Grub to a slave drive from which it will boot OK, Windows is much more fussy...

---

### Post by mo79 on 2006-09-28
Cool ;)

It's not dangerous (for want of a better word) to be going into the BIOS often to select the drive you want to boot from?
Guess not, as it's just another way of Grubbing - but still, I fear everything. :O

Cheers.

---

### Post by gn2 on 2006-09-28
You shouldn't have to actually go into the BIOS, just press whatever key brings up the boot device list.

Often this is F8.

If you want a completely safe separate hard drive/separate OS solution, PCLinuxOS has a graphical installer that will install to a USB hard drive, so you can enable USB HDD in the BIOS, then put it before the internal drive in the boot list, then when you don't want to boot Linux from the USB drive, just unplug it.

Just a pity that Ubuntu doesn't offer this facility.

---

### Post by mo79 on 2006-09-28
Ah cool ;)

I press F12 on startup to get the boot device menu, I guess that's different to going into the BIOS and is okay to do often?

Ordering my HD later tonight so I guess I'm not diverting now ;)

---

### Post by CatKiller on 2006-09-28
No, it's not dangerous. Unless you get the temptation to start fiddling with things that you shouldn't. I don't know how many BIOSes have the option, but mine (Award BIOS) has an option called HDD Boot Sprite that allows me to choose which drive I want to boot from at boot time. So my Windows drive has the NT boot loader, and my Linux drive has GRUB, and they're both completely oblivious to each other. So in principle, should either one break, the other will continue to function completely unchanged.

Even if you don't have that option, as gn2 says , you can still go into the BIOS and change the boot order every time you want to boot a different OS to the one you did before. Same effect, more button presses :)

With all of the computers I've had it's been Del to get into the BIOS. One of the F keys is quite common too. The only reason it won't say which button it is when the computer boots is if the manufacturer has put a boot splash screen over it. And if they have, they can tell you which button it is.

---

### Post by mo79 on 2006-09-28
Good to know - quite a few of my questions I realise are quite obvious, I just get nervous creeping out of the Microsoft pond; very rare for me tinker inside a machine too lol.

On my Dell, F12 opens up the boot menu to manually select a device and F2 takes me into setup where I can set a routine boot order.

...Just recording a reply for future worried well's like myself here. ;)

---

### Post by gn2 on 2006-09-28
> **mo79 said:**
> Ah cool ;)

I press F12 on startup to get the boot device menu, I guess that's different to going into the BIOS and is okay to do often?
)

Certainly is safe to press F12, and it *is* different from entering the BIOS. 

Be sure you take proper anti-static precautions when you open your case and install the hard drive.

Don't work in a carpeted room, and touch the metal work of the case with both hands before touching the hard drive. So long as you do this it's safe.

Also important to make sure PC is switched off.

---

### Post by mo79 on 2006-09-28
;)

Once the drive's installed I guess it will show up in Windows as working?..And then I can go and Ubuntu LiveCD boot and install..

---

### Post by gn2 on 2006-09-28
Once it is fitted in the case, connected to the IDE cable and molex power connector, it will be detected by, and shown in the BIOS.

You can now run the live CD (with the Windows drive unnplugged) and install to the new drive, as previously described.

---

### Post by CatKiller on 2006-09-28
> **gn2 said:**
> You shouldn't have to actually go into the BIOS, just press whatever key brings up the boot device list.

Often this is F8.

Excellent. Didn't know whether other BIOSes would have something similar, and I didn't know that it'd be implemented in such a handy way. You learn all sorts of unrelated stuff here. Cheers gn2.

---

### Post by mo79 on 2006-09-29
Me again - Hoping this will be the last...at least until my HD arrives.

Is there a difference between the GParted LiveCD and the one on the Ubuntu LiveCD? And what's the best way to allocate partitions for a 80GB (I assume it will be a few gigs less of that amount) drive?

I've sussed that about 40GB could be shared FA32, 1024 is Linux swap, so what about the other 6936? And if I partitioned using just a GParted LiveCD first, then how do I get Ubuntu to slot into these when installing?

---

### Post by CatKiller on 2006-09-29
> **mo79 said:**
> I've sussed that about 40GB could be shared FA32, 1024 is Linux swap, so what about the other 6936? And if I partitioned using just a GParted LiveCD first, then how do I get Ubuntu to slot into these when installing?

I think your maths is off - 40,000 - 1024 = 38976 :) Even then, it'll be something else because of the difference between how computers count and how hard drive manufacturers count.

If you've decided that you'd like 40 Gigs as FAT32 and 1 Gig as swap, just have the rest as one ext3 partition for /. It's the most straightforward, and it'll work.

Some people recommend the GPartEd disk over the Ubuntu live cd, but I've never had any problems with the GPartEd on the live cd. During the install process you get to select how you'd like the drive partitioned, formatted and mounted. It's all quite obvious, especially if you've already worked out your allocation as you have. If you select a mount point in /media for your FAT32 partition then you'll get an icon on your desktop for it. If you select a mount point anywhere else, you won't. It's a personal preference, really.

---

### Post by mo79 on 2006-09-29
Lol, I have no idea how I got my figure now or had the audacity to post it! Cheers ;)

---

### Post by mo79 on 2006-10-06
Okay, got my hard drive and am armed - but hopefully not dangerous! 
Just want to run by some partitioning scenarios, hopefully you can tell me what's best considering that I'm dual booting with WinXP on my existing drive and Ubuntu for my new, second, 80GB HD. Either (all roughly):

a)
Ubuntu / (ext3) = 10GB
Ubuntu / home (ext3) = 28,464MB
Swap / (linux-swap) = 1536MB
Shared Data (Fat32) = 40GB

As stated before I have 512MB RAM, getting another 512MB later in the year so is 1536 good or 1024 enough? I'd modify the above (or below) if so.

b)
Ubuntu / (ext3) = 5GB
Ubuntu / home (ext3) = 33,976MB
Swap / (linux-swap) = 1024MB
Shared Data (Fat32) = 40GB

or if the FSDrive utility is good for Windows to look at it too (if advisable..?)

c)
Ubuntu / (ext3) = 5GB
Ubuntu / home (ext3) = 73,976
Swap / (linux-swap) = 1024MB

In all scenarios, what's the best space to divide between Ubuntu and Ubuntu home? Or is it best like CatKiller said before to keep it simply, no 'home' part? i.e.

d) 
Ubuntu / (ext3) = 38,976MB
Swap / (linux-swap) = 1024
Shared / (fat32) = 40GB

Many thanks - and then surgery begins! ;)

---

### Post by CatKiller on 2006-10-06
I'd feel that 5 Gigs is just too tiny for your / partition. I know you've got a separate /home partition, but if you're like me then you'll be downloading all sorts of things through Synaptic, just to try them out. So I'd go for 10. In my limited experience, 1 Gig of swap should be sufficient. Go for more if you feel like it. I don't even know how to find out how much of mine I'm actually using.

As to the division between your /home and FAT32 partitions, it really depends on how you're going to use them. If you think you might end up with vast quantities of per-user stuff, make the /home partition bigger. If you think you might end up with vast quantities of stuff that lots of users might need to access from Windows, make the FAT32 partition bigger. Every time I've tried to guesstimate these things in the past, one of my partitions has been too small, and one has been to big, since I didn't end up using them how I thought I would starting out. Or I just ran out of room on all the partitions, which is what happened to me last time.

I have no idea how good or otherwise the driver for Windows ext support is. Sorry.

Pick a number. It doesn't ultimately matter which you choose - it's probably going to be the wrong one. At least with gparted you have a handy way of resizing the partitions once it becomes more apparent why your first number was wrong.

---

### Post by mo79 on 2006-10-06
Excellent. ;) I guess if my FAT32 partition doesn't get used as much I can just get rid of it.
Perhaps, I might just keep my install simple with just a root and swap, so folders and stuff grow naturally, or is there a distinct benefit of home?

---

### Post by Sef on 2006-10-06
For your scanner, check out the Umax page, on the [sane-project.]("http://www.sane-project.org/cgi-bin/driver.pl?manu=umax&model=astra+slim&bus=any&v=&p=")

---

### Post by CatKiller on 2006-10-06
In principle, it makes it easier to backup, use with a new distro, and is tidier. I don't have a separate /home partition though, so there may be wondrous advantages I haven't seen. Either way, you can change to the other approach later.

---

### Post by mo79 on 2006-10-06
Excellent, think I'll leave /home for now. I wish it wasn't 11pm here, or that I had more energy to open my comp right now! ;) I know a good bit about what expect, so hope to one day subvert my girlfriend's iMac to Xubuntu, after some RAM and a bigger HD.

---

### Post by CatKiller on 2006-10-06
Good luck. Remember that computers won't work unless you offer them a blood sacrifice, and it's the magic smoke that makes them work. Don't let it out.

---

### Post by mo79 on 2006-10-06
Gah, I'll eventually click 'Install' lol.

I just discovered that on my Boot Menu (and also the BIOS Boot Sequence option) you can only choose between the first HD (Windows), the first CD drive or the floppy...

Does that mean I'd be better off following this: [http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
(I have a Dell Dimension 4550 like him)

Or can it still be done the way gn2 said?...I've put the second drive in, the BIOS and Windows recognises it, but I haven't done anything with it yet, so would it somehow become 'noticed' by Dell Boot Menu/Sequence once I put Ubuntu on it?

It's terrible being British. Too much pessimism! :( 

Zzz

---

### Post by CatKiller on 2006-10-06
The key stage from what gn2 told you is to **disconnect** the Windows drive **before** you install Ubuntu. Keep the drives as separate as possible. It is reasonably likely that GRUB would install itself to the MBR of the Windows drive out of mischief. Then you'll be grumpy.

Keep them seperate for the install. You can work out how to boot the one you want afterwards. Just concentrate on getting them each to boot individually.

And it's great being British! Although that might just be the Lemsip talking.

---

### Post by gn2 on 2006-10-06
Once the 2nd drive's in and the Windows drive's unplugged, just clean install the Ubuntu and accept the default partitions.

You can always change partitioning later if need be.

---

### Post by mo79 on 2006-10-07
Cool, kinda...I removed the Windows drive entirely for the install but when I started to install Ubuntu, it just hung, couldn't create a file system...
So, I plugged in Windows (whew, when it came back to familiar ground!) and here I am. Now the new drive doesn't even show up in Windows, so er what now?
Should I use Seagate's Discwizard or?... :(

---

### Post by CatKiller on 2006-10-07
At which point did it hang? There are a number of posts with solutions about problems during the install process.

---

### Post by mo79 on 2006-10-07
When it was creating the Ext3 partitions. I watched the bar until 6% then made some tea :)
I come back and it's rested at 5% and then it errors. Then it somehow tries to install but is clearly not doing anything.

---

### Post by gn2 on 2006-10-07
Re-boot and try again?

---

### Post by mo79 on 2006-10-07
I did, but now it hangs at the point where it would show you the HD's you can install to...This is nightmarish, but I'm happy I didn't mess with my Windows drive.

I didn't run Seagate's DiscWizard software when I installed the new HD, I just loaded from the LiveCD after the BIOS verified it. What now? :| Hope I haven't mucked up the new drive!

---

### Post by gn2 on 2006-10-07
Try downloading the gparted live cd, and completely delete all partitions on the drive, then create one logical partition using the whole drive.

Then re-try installing Ubuntu accepting default partitions.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Remember to disconnect the Windows drive first to prevent nasty things happening!

---

### Post by mo79 on 2006-10-07
Thanks ;)

My hands are clammy but I always sigh relief, so far..

---

### Post by gn2 on 2006-10-07
> **mo79 said:**
> Thanks ;)

My hands are clammy but I always sigh relief, so far..


Just so long as you keep that (still working) Windows hard drive safe from harm......

Stick with it, you'll get there eventually!

---

### Post by mo79 on 2006-10-07
Off on a little break but I won't give in!

BTW, do you mean create one logical ext3 partition?

---

### Post by gn2 on 2006-10-07
> **mo79 said:**
> Off on a little break but I won't give in!

BTW, do you mean create one logical ext3 partition?

Previously when I've had trouble getting Ubuntu (or other OS to install I have used Partition Magic to create a new partition as Fat32, and installing has worked.
No reason why ext3 shouldn't either.

---

### Post by mo79 on 2006-10-07
No luck :( This is much trickier than I thought it would be, having doubts about persisting.

GParted LiveCD reports 'An Error Occured While Applying The Operations', thought I'd try Ubuntu installer again and it writes the ext3 'til  about 16%, stops, and then hangs at 5% when making partitions.
Any suggestions? I might try once more tomorrow.

---

### Post by CatKiller on 2006-10-07
It sounds like a hard drive problem. If the cables and jumpers are difinitely fine - check them, it's easy to knock cables when you're inside the case, and the jumper setting that was appropriate for both drives might not be for just the one - then most hard drive manufacturers have utilities you can download as boot floppies to run some vigorous tests on the drive, and to partition it quickly. That might help.

---

### Post by gn2 on 2006-10-07
Are the fans running OK, and is the CPU cooler clear of dust?

---

### Post by mo79 on 2006-10-07
I think the cables/jumpers are fine. I even ran the drive using the master connector. Both HD's are on cable select, factory preset and Dells like it that way.
Will have a look at Seagate now. Fans are fine, not too much dust in the case in general.

When I first installed the HD, and booted into Windows, it recognised it and gave it a driver. I'm not sure if it was the correct thing to do, but I uninstalled it prior to trying to installing Ubuntu (figuring it wouldn't recognise it again anyway).
But now there's no mention of it in Windows. GParted, the BIOS (though sees it as 'unknown drive' now) and Ubuntu LiveCD see it but that's about it. At minimum I'd like to get it back running as a FAT32 drive for Windows now first, just to see if it's all dandy.

---

### Post by gn2 on 2006-10-07
Suggest running manufacturer's utility.

Don't know about it, only use Hitachi or Samsung drives myself.

Perhaps it will sort it.

Gparted live CD should be able to create Fat32 logical partition.

---

### Post by mo79 on 2006-10-08
Well, today I turned on my computer (Windows-master, new-slave) and, er, Windows detected the new drive again and put the driver in, lol. I've no idea why it happened, but I don't question the Computer God when things go my way.
I want to step cautiously though - a friend has bought the official Ubuntu book for me to collect on Weds, so although my CD reports no errors on it, it might (at least in my head) be smoother with the DVD that comes with it?

Just want to ask, to test the drive, is it wise to use XP Disk Management to prepare it for use with Windows to check if it's just writing/reading fine?
The drive reports 7.62GB Unallocated, so would that maybe explain somehow why I've had troubles?...I'm not sure what I'm on about now, so you can pick up from here. :)

I will keep trying - just in more manageable chunks now!

---

### Post by CatKiller on 2006-10-08
> **mo79 said:**
> Just want to ask, to test the drive, is it wise to use XP Disk Management to prepare it for use with Windows to check if it's just writing/reading fine?

Pah. I wouldn't trust XP to do anything, which is why I've never used it. Use the manufacturer's diagnotic tools - they'll be tailored to any undocumented foibles of the drive. And I generally jumper my drives as Master/Slave, since in the past the Cable Select had problems. This may well not be an issue these days, but I've got into the habit. Oh, and a full check using the manufacturer's diagnostics will take some time. When I've used them in the past I've set them going and then gone to bed.

---

### Post by mo79 on 2006-10-08
Cheers will do that later tonight. If the utility says it's fine is there any other way I can approach Ubuntu installation?

Been Googling 'round a bit. The horror stories of people installing on the same drive as Windows make me glad I got a new hard drive, even if it's a minor task at mo.

---

### Post by CatKiller on 2006-10-08
> **mo79 said:**
> Cheers will do that later tonight. If the utility says it's fine is there any other way I can approach Ubuntu installation?

You could make the partitions in advance, either with a manufacturer's utility or the GParted cd.

---

### Post by mo79 on 2006-10-08
Lol...Er, well I only had to do the 90 second test and for each block of sectors it said 'Found Bad Sector' repeatedly, so no need for the full one then lol.
Seagate suggest I zero fill the hard disk with their utility and try again (I mailed 'em before I ran the diagnostics program), is that going to make any difference (did the failed installation do that?) or is it time to get this one swapped?

---

### Post by mo79 on 2006-10-09
Hmm, well I could only 'quick zero fill', I didn't see any response when it tried a full one. And the quick error checker found loads of bad sectors, while the full one hung on checking. I guess that's the hallmarks of a doozy.

And it all could've been so easy! ](*,)

---

### Post by gn2 on 2006-10-09
> **mo79 said:**
> Lol...Er, well I only had to do the 90 second test and for each block of sectors it said 'Found Bad Sector' repeatedly, so no need for the full one then lol.
Seagate suggest I zero fill the hard disk with their utility and try again (I mailed 'em before I ran the diagnostics program), is that going to make any difference (did the failed installation do that?) or is it time to get this one swapped?

Is it under warranty?

If so get it returned A.S.A.P. to retailer for either a refund or a Western Digital, Samsung or Hitachi.

You might get it going but there will always be nagging doubts, and the risk of total data loss......

---

### Post by mo79 on 2006-10-09
It is indeed. I think I might try a replacement one as some people are quite fond of Seagate, after that I'll go with WD who do my current one.
Here's hoping my next forum post will just be that of success!

---

### Post by gn2 on 2006-10-09
> **mo79 said:**
> It is indeed. I think I might try a replacement one as some people are quite fond of Seagate, after that I'll go with WD who do my current one.
Here's hoping my next forum post will just be that of success!

Believe Seagate do 5 year warranty on their drives. If you get a good one that's a plus.

For me it's Samsung first then Hitachi, but my choice is formed by the noise they make, nothing else.

---

### Post by mo79 on 2006-10-10
I'm 100% sure it's the HD as even Windows XP Disk Management refuses to initialise it (explains why Ubuntu/GParted didn't want anything to do with it too). SeaTools created an appalling bad sectors report on it, probably delivery damage.

I'll probably be fine once a working drive arrives but is it worth downloading the alternative CD or is there not much benefit in that?

---

### Post by gn2 on 2006-10-10
> **mo79 said:**
> I'm 100% sure it's the HD as even Windows XP Disk Management refuses to initialise it (explains why Ubuntu/GParted didn't want anything to do with it too). SeaTools created an appalling bad sectors report on it, probably delivery damage.

I'll probably be fine once a working drive arrives but is it worth downloading the alternative CD or is there not much benefit in that?

Wait till you get a working hard drive, then try standard install.

Only go for "alternative" CD if standard one gives problems.

No OS is going to install on a defective hard drive, it would be like trying to build a house on quicksand.

---

### Post by mo79 on 2006-10-12
Excellent, Ebuyer have verified the drive was bad!
In advance, I know how to set up dual booting one way for a Dell Dim. 4550  (BIOS/boot menu only allows you to choose master HD, so I'll be following [http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)) now,
but, just out of curiosity, is it possible to, say, have a boot floppy disk that will make it boot the slaved Ubuntu HD?
My comp can look at the floppy first, so if I have a boot to Ubuntu HD floppy in it it would boot to that, if not in it would go straight to Windows.
I know it makes no difference (the above link method seems less hassle!), but just wonder if it can be done (or even if with a bootable CD - though floppy being better in that you can eject the disk with the power off) - and if it would be safe? I'm not sure how to word what I mean for Google? :-k
If this method's possible I can likely bring another convert in! 

Still playing with the LiveCD - can't wait to have this on my computer! ;)

---

### Post by gn2 on 2006-10-12
> **mo79 said:**
> Excellent, Ebuyer have verified the drive was bad!
In advance, I know how to set up dual booting one way for a Dell Dim. 4550  (BIOS/boot menu only allows you to choose master HD, so I'll be following [http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)) now,
but, just out of curiosity, is it possible to, say, have a boot floppy disk that will make it boot the slaved Ubuntu HD?
My comp can look at the floppy first, so if I have a boot to Ubuntu HD floppy in it it would boot to that, if not in it would go straight to Windows.
I know it makes no difference (the above link method seems less hassle!), but just wonder if it can be done (or even if with a bootable CD - though floppy being better in that you can eject the disk with the power off) - and if it would be safe? I'm not sure how to word what I mean for Google? :-k
If this method's possible I can likely bring another convert in! 

Still playing with the LiveCD - can't wait to have this on my computer! ;)

Does the Dell 4550 BIOS give USB as a boot option? 
If so PCLinuxOS is an excellent option, as it gives install to USB as an option during set-up.

How do you know Dell 4550 will only list master as boot device, does it have two hard drives fitted yet? (Won't show drive that isn't there)
.

---

### Post by mo79 on 2006-10-12
Yeah, there's a USB boot option. Prefer to be a sheep and be with the Ubuntu clan though. ;)

When I had the now-returned new drive in - though faulty - both the BIOS (and I turned detection on) and Windows recognised it. I had a look to see if it came up in the boot menu and boot sequence, and it didn't (again it's the same in that you can only select the first CD drive in boot menu and boot sequence, not the second. I got that confirmed by Dell. It's a stupid thing but I guess that's what they have)!
But if I follow confused57's post I put Ubuntu on master but get it to have XP (slave) as the default choice on Grub (and with XP unplugged during installing, it's boot record isn't written over - and if I wanted to get rid of Ubuntu (unlikely), I just put XP back as master.

Would this be the kind of thing I'm after by any chance? [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php) if I did the floppy boot route?

---

### Post by gn2 on 2006-10-12
> **mo79 said:**
> Yeah, there's a USB boot option. Prefer to be a sheep and be with the Ubuntu clan though. ;)

Would this be the kind of thing I'm after by any chance? [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php) if I did the floppy boot route?

Super grub disk should be perfect for your needs.

Pity about the Dell BIOS.
.

---

### Post by mo79 on 2006-10-12
Thanks. ;) I think I'll follow confused57's method of drive-swap-and-config-editing method, but great to know that this can be done - a lot of Dell users out there!

Windows running off slave shouldn't be a problem should it? 

Thanks again. New drive should arrive shortly, hoping this one's fine. I think I've learnt quite a bit before even having it here!

---

### Post by gn2 on 2006-10-12
> **mo79 said:**
> a lot of Dell users out there!

Windows running off slave shouldn't be a problem should it? 



1: The power of marketing.... 
   I have a Dell, but I got it on eBay for £10. Wouldn't buy a new one...

2: Windows doesn't like being slave, Bill wants to be Master.
   Super Grub disk should sort that out though.  
.

---

### Post by CatKiller on 2006-10-12
> **mo79 said:**
> just out of curiosity, is it possible to, say, have a boot floppy disk that will make it boot the slaved Ubuntu HD?

It's more than possible - it's a fairly standard configuration to install GRUB to a floppy. In fact, I believe that the Alternate install will ask you where you want to put GRUB.

Good luck with the new drive.

---

### Post by mo79 on 2006-10-13
Indeed, as much as I like my Dell I did get it due to brand power. The boot menu/sequence restriction really is a joke. If say there was an OS that came on a DVD, and your DVD drive was your second drive, you would *have* to swap the drives 'round to get it to install lol! *sigh*
confused57 seems to be fine with XP on slave...Is it safe to just try still or not recommended? Seems a bit more tidy to not bother with a floppy, I think.

I think I deserve the award for the most questions pre-installing! :D

---

### Post by CatKiller on 2006-10-13
> **mo79 said:**
> confused57 seems to be fine with XP on slave...Is it safe to just try still or not recommended?

When I had a similar setup - installing Windows on one drive and then Ubuntu on a completely different drive - I ended up with Windows 2000 on a slave drive, and that worked fine. I don't see any reason why Windows XP would be any different.

---

### Post by mo79 on 2006-10-17
Hooray! :D

New drive came today, unplugged XP, made new drive master and put Ubuntu on it. Did some Terminal doo-daa (I shall call things that for a while) and I can default boot into XP unless I choose Ubuntu.  And yet XP boot record has not been touched. I could put XP back as master and it would never know Ubuntu was there.
One thing though is, in Ubuntu, when idle, just 'froze' with a honeycomb kind of screensaver frame...don't know if it was a one off but what can I do about that?
Other than that all's sweet. Got my Ubuntu book and dipping in nice and slow. This is how I wanted my system to be set. Thanks all! ;)

---

### Post by gn2 on 2006-10-17
> **mo79 said:**
> Hooray! :D

New drive came today, unplugged XP, made new drive master and put Ubuntu on it. Did some Terminal doo-daa (I shall call things that for a while) and I can default boot into XP unless I choose Ubuntu.  And yet XP boot record has not been touched. I could put XP back as master and it would never know Ubuntu was there.
One thing though is, in Ubuntu, when idle, just 'froze' with a honeycomb kind of screensaver frame...don't know if it was a one off but what can I do about that?
Other than that all's sweet. Got my Ubuntu book and dipping in nice and slow. This is how I wanted my system to be set. Thanks all! ;)

Screensavers freezing the PC is all part of the rich experience of Ubuntu.

You probably need to install the correct graphics drivers. (or disable the screensaver)

Enjoy.

---

### Post by CatKiller on 2006-10-17
Glad you're all up and running. Enjoy your new existence as a Linux user.

---

