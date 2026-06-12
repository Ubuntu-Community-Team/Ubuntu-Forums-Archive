---
title: "Pimp my Ubuntu ride: PC on the way, and I want to be ready!"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by growingfreedom on 2008-01-22
I'm getting a refurbished Dell in a few days, and I plan to install Ubuntu as my main OS. Want to help me get ready?

> Inspiron Desktop 531 Mini-tower: AMD Athlon 64 X2 Dual-Core 5600+ (2.80GHZ) Genuine Windows Vista Home Premium

Oh yeah, Vista is either getting the hatchet straight away, or better yet is moving to a partition of its own.

A little background, so you know what kind of help might be useful to me: 

I'm not a total newb to linux installs, but I might as well be. Its been several years since I had a linux machine to play with, and back then I didn't do a whole lot with it except finish all my CSCI classes. I'm a computer consultant for home and small business solutions. Your neighborhood 'computer guy' is the best way to describe what I do: web dev, wireless setups, a little database work, security, etc..

So, here is what I was thinking as an ultimate setup for this new machine, OS wise:

Triple / Quad boot: Ubuntu, XP, Vista, and a 'play with OS's' partition. Plus 2 backup partitions = 6.

I'd like to have XP and Vista so I can test solutions for my clients without logging into their machines remotely. That tends to spook some of them :).

What can I do to get ready for my install? How should I gracefully 'bump off' Vista? As I remember, its not too hard to shuttle off and repartition in quality linux distros. Are there a few articles I should read along these lines? (Lilo, fdisk, etc..?).

Thanks, and I'll definitely follow up any suggestions you make.

-Growing Freedom :)

---

### Post by wolfen69 on 2008-01-22
if you're going to do a multi-boot better if xp is installed first, then vista, then ubuntu.
by installing ubuntu last you insure that GRUB will do it's job and give you a choice of OS's at startup.

by having a "play with OS's partition", you will create headaches for yourself. example: you decide you want to install mandriva. the install goes fine and you reboot. you say "what happened to ubuntu or vista in grub?" because the new distro did not correctly identify your other installs. (trust me on this)

get a seperate hard drive for testing and unplug your main drives while fiddling/installing  a new OS. i leave off the side of my case so i can easily reach in and unplug my main drives and plugin the test drive. or stick with live cd's for "testing" or install virtualbox inside of ubuntu.(one of my favorite ways to test a new distro) you will probably need 2 gigs of ram for this. anyway, i hope this helped. good luck.

---

### Post by PurposeOfReason on 2008-01-22
Actually, with three OS's it would be best to get a gparted CD and set that up first. Especially with vista and how it hates to be touched.

---

### Post by jesusfreak107 on 2008-01-22
Well, looking at your post, it looks like the fist thing you need is a good partitioner.  For this, I recommend the [Parted Magic LiveCD]("http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html?tag=lst-8").   It is an iso file that you will need to burn to a CD (with the appropriate software, you cannot just burn it on there. google for an "iso file burner"). You can then boot off of the CD. it is a 36MB mini-OS that has a ton of hard drive tools.  With it, you can partition your hard drive into however many partitions you want, and never mess up any existing OSs. I did it just yesterday. I now have two OSs on a 60GB HDD: WinXP (on there from the start), and Xubuntu (installed on a newly-created 20GB partition.  

Also, by the "Pimp" part of the question, I assume you are looking for some neat stuff to install on Linux, like a 3D desktop switcher, etc? well... welcome to... [The Beryl Project]("http://www.beryl-project.org/features.php"). it is the ultimate graphical enviroment for Linux, while still being ultra-usable and customizable.  I have not used it, because my current computer (saving for a Dell XPS 420) is a peice of crap, although I have heard very good things about it, and seen UNBELIEVABLE video demonstrations of it. 

Also, you might want to decide what version of Ubuntu you want.  There are three that you would want to choose from:

[Xubuntu: Performance]("http://www.xubuntu.org/")
[Ubuntu Desktop Edition: Basic User]("http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition")
[Kububtu: Graphics]("http://www.kubuntu.org/") (would go good with Beryl)


I hope this helps!

:guitar:

---

### Post by growingfreedom on 2008-01-22
> **wolfen69 said:**
> if you're going to do a multi-boot better if xp is installed first, then vista, then ubuntu.
by installing ubuntu last you insure that GRUB will do it's job and give you a choice of OS's at startup.

by having a "play with OS's partition", you will create headaches for yourself. example: you decide you want to install mandriva. the install goes fine and you reboot. you say "what happened to ubuntu or vista in grub?" because the new distro did not correctly identify your other installs. (trust me on this)

get a seperate hard drive for testing and unplug your main drives while fiddling/installing  a new OS. i leave off the side of my case so i can easily reach in and unplug my main drives and plugin the test drive. or stick with live cd's for "testing" or install virtualbox inside of ubuntu.(one of my favorite ways to test a new distro) you will probably need 2 gigs of ram for this. anyway, i hope this helped. good luck.

Thank you! That was hours of frustration avoided. A stitch in time. Well, several! Can I give more than :popcorn: ?

I dimly remember worrying about this with WindowsME , Mandrake, Debian on my current computer. I'm glad to know that the worry isn't unfounded, and what to do about it.

So as I see it:
[LIST=1]
[*]repartition
[*]install XP
[*]install Ubuntu
[*]configure for grub / lilo boot options
[*]cross fingers
[*]knock wood
[*]boot each and play
[*]use the old computer to play with OS's
[*]remember to help others to repay this advice!
[/LIST]
Thanks again!

-Growing Freedom

---

### Post by growingfreedom on 2008-01-22
> **PurposeOfReason said:**
> Actually, with three OS's it would be best to get a gparted CD and set that up first. Especially with vista and how it hates to be touched.

This is good to know. I'd remembered using Mandrake to do the partitions as part of the install process. It seems this is 'out of style' with the Vista-monster. Any other advice for touching that untouchable partition, so as to not-break it?

---

### Post by growingfreedom on 2008-01-22
> **jesusfreak107 said:**
> Well, looking at your post, it looks like the fist thing you need is a good partitioner.  For this, I recommend the [Parted Magic LiveCD]("http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html?tag=lst-8").   It is an iso file that you will need to burn to a CD (with the appropriate software, you cannot just burn it on there. google for an "iso file burner"). You can then boot off of the CD. it is a 36MB mini-OS that has a ton of hard drive tools.  With it, you can partition your hard drive into however many partitions you want, and never mess up any existing OSs. I did it just yesterday. I now have two OSs on a 60GB HDD: WinXP (on there from the start), and Xubuntu (installed on a newly-created 20GB partition.  

Also, by the "Pimp" part of the question, I assume you are looking for some neat stuff to install on Linux, like a 3D desktop switcher, etc? well... welcome to... [The Beryl Project]("http://www.beryl-project.org/features.php"). it is the ultimate graphical enviroment for Linux, while still being ultra-usable and customizable.  I have not used it, because my current computer (saving for a Dell XPS 420) is a peice of crap, although I have heard very good things about it, and seen UNBELIEVABLE video demonstrations of it. 

Also, you might want to decide what version of Ubuntu you want.  There are three that you would want to choose from:

[Xubuntu: Performance]("http://www.xubuntu.org/")
[Ubuntu Desktop Edition: Basic User]("http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition")
[Kububtu: Graphics]("http://www.kubuntu.org/") (would go good with Beryl)


I hope this helps!

:guitar:

I'm sure it will help.

I'm familiar with repartitioning. Do it all the time for clients so they have less chance of destroying themselves and their data (backups, restore images, etc..). I wouldn't have thought of doing this first, but it makes perfect sense. I'd hoped to be able to handle it all during the install, but I can see that is probably unwise....

The 'pimp' part was to ask for suggestions that might fit my machine and purposes. I think, judging from replies and research so far, that I've come to the right place to find answers.

Thanks so much,

Grok Freedom. Grow it!

---

### Post by jesusfreak107 on 2008-01-22
yes, this is definitely the place to get answers. to all of my posts, I get a reply in under 2 minutes. it is almost an IM system with several thousand people online looking for people to help, at the same time

oh, btw, to everyone, instead of saying "thanks", you can click the little award button next to the "quote" on a reply, and it will be put into that person's record that something that they said was helpfull. Not to try to get undue attention here, I have noticed it elsewhere, too.

---

### Post by Arthur Archnix on 2008-01-22
My two cents:

Use Gparted to create partitions before hand (as above).
Primary partition 1
5GB {XP}
Parimary partition 2
10GB {Vista}
Remaining Drive Extended Partition
7GB {Ubuntu} Root and Home both go here 
7GB {Empty} For play OS 
1GB {Swap}
Remaining space is for Data, make it NTFS

Installation order is correct above, XP, Vista, Ubuntu. Don't worry about new installs messing up your grub, when it comes time to install a new bootloader just say no thanks. Then go into grub and add an entry manually for the new OS.

Hopefully you've got a real Vista DVD, and not the Dell one that it comes with. Those tend to just want to reinstall the whole drive. If that's the case, before blowing away your Vista install use vista tools to shrink partition. When it won't shrink anymore, defragment, reboot using gparted and shrink by no more than 30%. So, if you vista is 60GB you don't want to try and make it 10GB right away. Make it 45. Reboot, defragment, repeat process until you have the size you want. Then use PING (Ping is not ghost) to create a bootable image of the vista partition. Once done, use Gparted to create partitions for your new setup making sure that the vista partition is the EXACT same size as the partition you created a ping image of. Install XP, use ping to put vista image on second partitino. Install Ubuntu.

Good luck!

---

### Post by growingfreedom on 2008-01-22
> **jesusfreak107 said:**
> yes, this is definitely the place to get answers. to all of my posts, I get a reply in under 2 minutes. it is almost an IM system with several thousand people online looking for people to help, at the same time

oh, btw, to everyone, instead of saying "thanks", you can click the little award button next to the "quote" on a reply, and it will be put into that person's record that something that they said was helpfull. Not to try to get undue attention here, I have noticed it elsewhere, too.
Thanks :)

I didn't notice that. I'll stop thanking everyone and just award them....well, crap, I can't help it!

---

### Post by growingfreedom on 2008-01-22
> **Arthur Archnix said:**
> My two cents:

Use Gparted to create partitions before hand (as above).
Primary partition 1
5GB {XP}
Parimary partition 2
10GB {Vista}
Remaining Drive Extended Partition
7GB {Ubuntu} Root and Home both go here 
7GB {Empty} For play OS 
1GB {Swap}
Remaining space is for Data, make it NTFS
The reason to put XP ahead of Vista is?
> **Arthur Archnix said:**
> 
Installation order is correct above, XP, Vista, Ubuntu. Don't worry about new installs messing up your grub, when it comes time to install a new bootloader just say no thanks. Then go into grub and add an entry manually for the new OS.

I'm pretty careful about things like that, and think I can handle not installing new bootloaders. I can see why, on general principle, it wouldn't be good advice-to-newb, but since I understand the packages to some degree, I just might go ahead with it this way.
> **Arthur Archnix said:**
> 
Hopefully you've got a real Vista DVD,
Er, I could get it, but I'd hoped to avoid the hassle. I'm expecting the standard Dell blue disks of doom. > **Arthur Archnix said:**
> and not the Dell one that it comes with. Those tend to just want to reinstall the whole drive. If that's the case, before blowing away your Vista install use vista tools to shrink partition. When it won't shrink anymore, defragment, reboot using gparted and shrink by no more than 30%. So, if you vista is 60GB you don't want to try and make it 10GB right away. Make it 45. Reboot, defragment, repeat process until you have the size you want. Then use PING (Ping is not ghost) to create a bootable image of the vista partition. Once done, use Gparted to create partitions for your new setup making sure that the vista partition is the EXACT same size as the partition you created a ping image of. Install XP, use ping to put vista image on second partitino. Install Ubuntu.

Good luck!
I've done this (copied images to new partitions) before with Windows installs. Glad to know that it'll work with Vista. I don't look forward to the resize process you outline, but I'm so glad to know how to do it! Another 5 hours saved. You're the best!

---

### Post by Arthur Archnix on 2008-01-22
> **growingfreedom said:**
> The reason to put XP ahead of Vista is?

If you add your vista install from a bootable DVD image, none. If you install it and it's content with the 10GB or so you give it via gparted then it will make booting the three OS's easier. More certain that things will work out of the box, as it were.

> I'm pretty careful about things like that, and think I can handle not installing new bootloaders. I can see why, on general principle, it wouldn't be good advice-to-newb, but since I understand the packages to some degree, I just might go ahead with it this way.

I installed Fedora8 and let it install a new boot-loader, and it didn't detect my previous Ubuntu install. Strange. From then on I just make entries manually.

> Er, I could get it, but I'd hoped to avoid the hassle. I'm expecting the standard Dell blue disks of doom.
Hopefully they let you install to a 10GB or whatever partition. Otherwise you'll be faced with reinstalling over the entire disk (and your new XP install) and be back at square one looking up PING on the google. :)
 
> I've done this (copied images to new partitions) before with Windows installs. Glad to know that it'll work with Vista. I don't look forward to the resize process you outline, but I'm so glad to know how to do it! Another 5 hours saved. You're the best!
Perhaps. It depends on what kind of discs you get. Could be hours saved, or hours wasted. I like knowing having a bootable image of my drive, and PING makes it silly easy. The PITA process is cautious, but makes it more certain that you won't lose any data. Plus I read somewhere that MS puts some partition image at the half-way point of the drive, shrinking by more than 50% would cause failures of epic proportions. I read that on the intarwebs though, so take it for what it's worth or read further if you're interested. I'm just outlining the process that had led to my 100% positive experience, A++ would partition again!! 

Either way, it doesn't sound like you're going to have any problems.

Unless you have multiple hard-drives? One hard-drive = easypeasy. Two hard-drives with Ubutu installed to a different hard-drive... sad times.

---

### Post by wolfen69 on 2008-01-23
**Arthur Archnix**:

> Unless you have multiple hard-drives? One hard-drive = easypeasy. Two hard-drives with Ubutu installed to a different hard-drive... sad times.

why is that?

---

### Post by growingfreedom on 2008-01-23
I have multiple drives, but never put multi-os's on multi-drives. The extra drives are always data or images only.

I think I'll just fire up the disks they send with the machine and see what kind of install hell it wants me to go through. If it looks like I can do some resizing from the install, I will, otherwise I'll exit and try the resizing / repartitioning scheme you outlined above.

---

### Post by Arthur Archnix on 2008-01-23
Just personal experience here and on #ubuntu. So many people coming in talking about how one OS or the other won't book. Do a little googling, or the scan the forums for Grub, or hang out in IRC for a couple hours. 

Like noted above, I'm just sharing my experience. Grub installed onto a system with multiple OS's that span multiple disks... well, I've seen things work less often, but as they're related to me I don't talk bad of them.

---

### Post by PurposeOfReason on 2008-01-23
> **growingfreedom said:**
> This is good to know. I'd remembered using Mandrake to do the partitions as part of the install process. It seems this is 'out of style' with the Vista-monster. Any other advice for touching that untouchable partition, so as to not-break it?
How I did it is I set up two partitions, one ntfs and one ext3. Installed vista. At the beginning of the vista install is gives you the choice (use continious or partition) choose partition and take half of your ntfs. Give the other half to xp when you install that. Finally, install ubuntu on the ext3 (choose manual instead of use continious) and you're set.

---

### Post by zabien1970 on 2008-01-23
> **growingfreedom said:**
> 

Er, I could get it, but I'd hoped to avoid the hassle. I'm expecting the standard Dell blue disks of doom. 


I'd be surprised if dell ships any disk since they expect you to use the recovery partition.
I wiped my HD installing ubuntu and when I called dell and had them send me the xp disk it put a bare install on my laptop, wifi wouldn't work, dvd's wouldn't play, disk of doom is right

---

### Post by Tekno_Cowboy on 2008-01-23
I've had no issues installing to multiple hard drives, even with some being sata, some ide, and some usb flash drives. You just need to point grub in the right direction, or if you don't want to dig into grub, super grub disk. Herman has a very good page on grub, linked in his signature.

---

### Post by Arthur Archnix on 2008-01-23
> **Tekno_Cowboy said:**
> I've had no issues installing to multiple hard drives, even with some being sata, some ide, and some usb flash drives. You just need to point grub in the right direction, or if you don't want to dig into grub, super grub disk. Herman has a very good page on grub, linked in his signature.

I'm not claiming this to be a grub problem. There's no bug-reports that I can find of grub misbehaving. If configured properly, you're absolutely right. But, from what I've seen on the forums and elsewhere, defaut Grub installs are less successful in cases of multiple OS over multiple HD's. I don't intend these comments to be the last word on the subject; just a note of caution that extra work may be required for some people in this situation. And troubleshooting it after the fact, for me at any rate, has proven to be harder than simply avoiding the risk altogether by aiming for simpler grub installation setups, either unpugging windows disks at the time of install and making the ubuntu disk first, plugging in and adding grub info manually afterwards, or putting the OS's on one disk. I'm sure other people with more Grub knowledge can explain the commands to redirect the target disk of grub installs and fix the problems when they arise, though again, this is a post-install fix since I've not found a way to reconfigure the grub installer that ships with ubuntu install disc.

Sorry to the OP if this is an off-topic distraction.

---

### Post by growingfreedom on 2008-01-23
> **jesusfreak107 said:**
> Well, looking at your post, it looks like the fist thing you need is a good partitioner.  For this, I recommend the [Parted Magic LiveCD]("http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html?tag=lst-8").   It is an iso file that you will need to burn to a CD (with the appropriate software, you cannot just burn it on there. google for an "iso file burner"). You can then boot off of the CD. it is a 36MB mini-OS that has a ton of hard drive tools.  With it, you can partition your hard drive into however many partitions you want, and never mess up any existing OSs. 

I made a couple boot CD's with Parted Magic. Hadn't used that before. Very nice and clean. My one beef is that the partition tool can't read volume names if they are FAT. (reads NTFS though I think). However, there is another tool on the tools section that gets partition tables, names and all, so together its looking like a nice lightweight partition solution. Thanks again.

-Growing Freedom

---

