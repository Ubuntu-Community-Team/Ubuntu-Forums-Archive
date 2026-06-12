---
title: "Has Ubuntu ever killed Windows in a dual-boot setup?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Zedison on 2007-06-18
I'm preparing to install Ubuntu 7.04 on my primary hard drive, and set up a dual-boot between it and Windows XP. But before I do it, I need to know whether this stands a chance of killing Windows or causing Windows to kill itself. What with the crazy nonsense I've seen out of XP lately, I wouldn't put it past it.
The first problem is partitioning... The entire hard drive is formatted with one single NTFS partition, and although less than a quarter of it is full, I've read that NTFS support doesn't work very well. I would need to be sure that letting Ubuntu's installer resize it automatically won't somehow screw it up.
The second problem is knowing how well Windows will get along after Ubuntu is installed. Will it safely exist in its own little world, or will it somehow tangibly affect the Windows partition? Is Windows going to notice anything and attempt to "fix" it (read: make things worse) or just hum along?

I do have complete back-ups of all my data, but I want to avoid a nasty surprise down the road.

---

### Post by Bachstelze on 2007-06-18
The partition resizing is the only that that could go wrong. Be sure to defrag your partition in Windows before and backup any valuable data.

---

### Post by atria on 2007-06-18
Resizing works fine for me, no problems whatsoever.

Ubuntu will not screw up your windows partition automagically. You will be able to read the files in your windows partition but not write to them, as the partition is mounted read-only. So its going to be pretty safe in that regard.

If you need ntfs write support which is stable now, check out ntfs-3g. It works perfectly for my 500gb ntfs volume.

---

### Post by joe.turion64x2 on 2007-06-18
Use Gnome Partition Editor (available in Ubuntu live CD) to resize your NTFS partition. It works quite well, but defrag first and back up.

Joe.

---

### Post by some_random_noob on 2007-06-18
> **Zedison said:**
> 
The second problem is knowing how well Windows will get along after Ubuntu is installed. Will it safely exist in its own little world, or will it somehow tangibly affect the Windows partition? Is Windows going to notice anything and attempt to "fix" it (read: make things worse) or just hum along?

I installed Windows and then installed Ubuntu (Dapper Drake) afterwards and had no problems. Shouldn't be any different with newer versions either. If Ubuntu does kill Windows then it will happen after the installation, apart from that they shouldn't interfere with each other while running.

The only thing I'd worry about is resizing the partition.

---

### Post by joe.turion64x2 on 2007-06-18
Yes, and the only think Windows can do is to run a routine to check the new partition size. Quite normal and automatic.

Joe.

---

### Post by Zedison on 2007-06-19
It happened.

I decided to use GParted to resize the NTFS partition instead of allowing the installer itself to try it, and I got a nasty surprise. The partition still exists, but somehow it is no longer bootable.

The Live CD was able to read from it and copy files off of it, and it even set up an option in GRUB to boot to Windows. Except Windows simply does not boot. 
Ubuntu itself knows the partition exists, but refuses to read from it, unlike the Live CD. I get a denial error when I attempt to check it out:

Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy
hal-storage-fixed-mount refused uid 1001

---

### Post by ElEdwards on 2007-06-19
I followed the advice here on the boards and had no problems.  I have a Presario 2170us with a 40-gig HDD.

Here's the order I did things in, based on the advice on these boards.

FIRST, I defraged & rebooted Windows three times.

SECOND, I backed up to CD any Windows files that were precious to me.

THIRD, I used the GParted Live CD to reduce my NTFS partition from 20Gig to 14Gig.... and then set up a 15Gig **/home** partition, a 10Gig **Linux** partition and a 1Gig **Swap** partition.

FOURTH, I rebooted Windows and let it do it's disk check and then boot normally.

FIFTH, then finally, I installed Ubuntu 7.04

..... and have had absolutely no issues or problems! :D

---

### Post by floke on 2007-06-19
First, did you get any errors or anything in the partitioning process?
Second, are you trying to mount the NTFS partition using 'sudo' - quickest way to try this is to open the terminal and type 'sudo nautilus' - then navigate through to the partition - if its automatically mounted it will be in the /media directory and see if you can access it.

Be careful though - and don't change anything while your using the 'sudo' command. Once you've checked it out just shut the window and report back.

---

### Post by LaRoza on 2007-06-19
If you are worried about Windows, you can resize the Windows withing Windows and install to the freed space.

---

### Post by Zedison on 2007-06-19
GParted gave me a warning after I attempted to resize the NTFS partition, saying that it couldn't be completed. That's probably why Windows isn't booting for me.

I can still read the partition (after realizing I had to change some permissions in order to do so) but when I attempt to boot to it from GRUB, absolutely nothing happens.

---

### Post by vexorian on 2007-06-19
If you want to play safe, you can resize your windows partitions from XP using the administrator tools\disks sections.

I freed 20GB for my ubuntu with those, did not have any problem using the 20GB space to create new partitions for Ubuntu during the installation.

Edit: couldn't see your last post.

If you can still read your partition, then you should not worry, you must get the windows XP cd and go to recovery console.

Then you should try issueing a fixboot command from there.

Notice it will make your computer boot from another partition, not grub, you will need to use the live-cd later to re install grub in the disk so you enable ubuntu as well


edit II: if fixboot alone doesn't change the situation you will have to use fixmbr

---

### Post by floke on 2007-06-19
Here's the thing. I have resized partitions so many times now that I have lost count. It has only EVER EVER gone wrong (even remotely) once - and it was like this.

What happens in the resize process is that the partitioner sometimes mounts the partition part of the way through the process, and then can't complete the process because the partitioner is mounted. Its the dumbest dumbest dumbest thing I have ever seen in Linux, but there you go. I will NEVER use the Feisty partitioner for this reason; will only ever use the Gparted tool on the Edgy live cd, since it's the only one I trust :(

Unfortunately I could not get the problem fixed and ended up doing a complete reinstall of Windows, and then ubuntu (using the Edgy livecd). 

You could also try the alternative (text based - i.e. non live cd) installer. I have used this many times and it has never given me any problems (probably because it doesn't try to mount the partition half way through the damn process).

Sorry to be the bearer of potential bad tidings on this one, but I couldn't solve it.

The good news though - is that resizing a NTFS partition *will* absolutely work for you - so don't be disheartened. You have been *incredibly* unlucky on this one.

** EDIT : From reading previous post it may well be possible to fix it - I have to confess that I didn't try for very long - it wasn't my PC and I needed to get it working a.s.a.p **

---

### Post by Zedison on 2007-06-19
Tried "fixboot" via the Windows Recovery Console. Seems to have done nothing.

I don't want to mess around with the MBR just yet until I'm sure it's the only way. Steve.K, did you attempt to do a Repair install of Windows, or did you just overwrite it with a totally new installation? What did it do to the boot loader?

---

### Post by oilchangeguy on 2007-06-19
quote- "What with the crazy nonsense I've seen out of XP lately" don't blame the os, sounds like operator error, not operating system error. and as other posters have said, ubuntu will not kill windows. again this would be caused by operator error, and not operating system error.

---

### Post by floke on 2007-06-19
I used the rescue discs that came with the PC. Tried to find a recovery console. Then thought **** it and reformatted the whole drive. I'd have a play to try and fix it first though, since this is definitely a last resort :shock:

But really, if you have to do this then don't be put off trying ubuntu again. As I say, you've had severe bad luck with a crappy partitioner. Use the alternative install next time and you'll be fine.

---

### Post by oilchangeguy on 2007-06-19
> **Steve.K said:**
> I used the rescue discs that came with the PC. Tried to find a recovery console. Then thought **** it and reformatted the whole drive. I'd have a play to try and fix it first though, since this is definitely a last resort :shock:

But really, if you have to do this then don't be put off trying ubuntu again. As I say, you've had severe bad luck with a crappy partitioner. Use the alternative install next time and you'll be fine.

factory restore disc's do not give you the option to enter the repair console. they are designed to do one thing. restore the computer to the original factory setup. a windows only disc is the only way to get to the repair console.

---

### Post by ElEdwards on 2007-06-19
I may be wrong (and probably am) but I think the partitioning problems have been reported using GParted from the Ubuntu Live CD but **not** from the GParted Live CD. :)

I downloaded and burned the GParted Live CD and used that before using the Ubuntu Live CD.

Based on my experiences with Ubuntu and Wine on my laptop, I'm about to make my desktop PC Ubuntu-only! :D

---

### Post by Zedison on 2007-06-19
Personally, my motivation for getting Ubuntu was to *avoid* weird situations that arise from Windows XP. It tends to break in places I never notice until much later, and the solution is almost always "reinstall it", which is a massive chore once you factor in the seven-year-old installer followed by tons of updates and a high possibility that you'll have to reactivate. The only reason I'm bothering with keeping it as a dual-boot option is because I share this computer, and the transition will never be complete as long as there's still some reliance on software that only ever works under Windows.

To find out that I've just won the "lottery from hell" over this boot situation is like getting punched in the gut, but it's not a killer turn-off since I have backups of all my important files. It's still an oversight that needs to be corrected, though.


That said, I'd like to know whether or not Windows plays nice with GRUB during a reinstallation, or whether it's going to require its own boot loader to do it. That should help me decide which way to go, unless someone can come up with an alternative.

---

### Post by floke on 2007-06-19
If it can't be fixed then...
Reinstall Windows - wipe entire drive
Reinstall Ubuntu using alternative installer - quickest way to do it with partitioning
That's it

ubuntu will detect XP in grub just fine so don't worry.

---

### Post by Thorndeux on 2007-06-19
If you haven't started reinstalling everything yet try resizing the Windows partition first.

When I first installed Linux as a dual boot it screwed up my Windows XP, too - during the partitioning process (it was Suse, though, not Ubuntu). I managed to fix it by making the Windows partition 1MB smaller. After that it worked fine.

Hope you get it sorted out,
Thorn

---

### Post by themuddaload on 2007-06-19
frankly it is easiest to use 2 hard drives =) just hook up your windows drive as the slave, and away you go.

---

### Post by Zedison on 2007-06-19
For all Windows can care, the partition is pretty much doomed. I tried repairing/reinstalling it several different ways, but none of them worked. Finally, I managed to break the boot loader altogether by attempting to install a fresh copy of Windows. Thus, even if it could be saved, there's really no point, because everything is already backed up and I'd be looking at a full reinstall anyway.

The best course of action at this point would simply be to reformat and take care not to make the same mistake twice. And on that note, I seriously recommend that this incident is recognized and documented a little more explicitly, to spare others the hassle.

---

### Post by vexorian on 2007-06-19
> **Zedison said:**
> Tried "fixboot" via the Windows Recovery Console. Seems to have done nothing.

I don't want to mess around with the MBR just yet until I'm sure it's the only way. Steve.K, did you attempt to do a Repair install of Windows, or did you just overwrite it with a totally new installation? What did it do to the boot loader?
fixmbr is "safe",  it will just replace the mbr - again, then reinstalling grub is quite "easy" if you got a live-cd and internet access to read the instructions.

But I guess reinstalling is an easy way.

---

### Post by juantovarm on 2007-06-20
I have tried to install a dual boot ibm thinkpad t40, windows and linux on more than 10 occasions on the same laptop. Windows always dies. Blue screen, not bootable. Doesn't matter what distro, I have tried all ubuntu flavors since Dapper, Fedora, Debian, Mandriva.., I ALWAYS end up with the same result. Ended up telling the owner -a friend of mine- to choose between linux and m$ on that machine, because i didn't know what else to do...He chose windows

---

### Post by vexorian on 2007-06-20
Did you try resizing the partitions from windows?

---

### Post by Vadi on 2007-07-27
Same problem here. Windows simply can't mount anymore, not even safe mode works.

---

### Post by joe.turion64x2 on 2007-07-27
Has any of you considered a hardware problem? Specifically a hard disk failure in the Windows side?

I experienced one once, Windows wouldn't boot anymore and Linux reported the failure in a NTFS partition.

There is a command called badsectors which can test your hard drive.

Thanks.
Joe.

---

### Post by vexorian on 2007-07-27
> **Vadi said:**
> Same problem here. Windows simply can't mount anymore, not even safe mode works.
It would be nice describing it a little more, for example, do you get to the windows menu in which you can choose safe mode? And have you run defrag before installing ubuntu?

---

### Post by thefoolisme on 2007-07-27
Not once in this thread, have I seen this question, so I have to ask, when you resized the NTFS partition, did you shrink it from the end of the hard drive, or from the beginning?  If you cleared space at the beginning, then the Windows MBR wouldn't be able to find the partition, thereby causing all of the problems.  I have installed and uninstalled linux systems so many times on my PC, never once having it mess up windows.  Of course that doesn't mean it won't happen.  Just curious, because if you did take it from the front of the drive, maybe you can just put the partition back like it was.

---

### Post by tlg on 2007-11-16
> **juantovarm said:**
> I have tried to install a dual boot ibm thinkpad t40, windows and linux on more than 10 occasions on the same laptop. Windows always dies. Blue screen, not bootable. Doesn't matter what distro, I have tried all ubuntu flavors since Dapper, Fedora, Debian, Mandriva.., I ALWAYS end up with the same result. Ended up telling the owner -a friend of mine- to choose between linux and m$ on that machine, because i didn't know what else to do...He chose windows

I have a similar problem, also on several IBM T41 laptops.
Starting from a blank disc, I have installed Win XP, allowing it to set up its own partition using a portion of the disc.
Then I installed Ubuntu 7.04 telling it to use the free space when the Partitioner screen came up. The install all went well and Ubuntu runs fine.
When I boot the machine I get the grub menu as expected.
If I select the Windows item in the menu, it blue screens, complaing about the disc partition not being bootable. No option but to restart the machine.

I have this situation on several different machines now, and it seems to me that the Ubuntu install is not dealing with the existing Win partition correctly. 

Curiously, I have one machine which dual boots just fine, and the install procedure was essentially the same. So there does not seem to be a problem with the machine type itself.

While these machines are primarily used with Ubuntu, we simply have to be able to boot Win for some particular apps.

I have seen a similar problem reported about RH Fedora Core 2 here:
[http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/)

Could it be the same problem:
"Windows fails to boot because Fedora Core 2 
altered the hard disk geometry as reported by the drives partition table.
"
Is it worth trying the solution mentioned here using sfdisk?

Alternatively, where should I look for the differences between the machine that works and the ones that don't?

Any help welcome!!

---

### Post by Sims2789 on 2007-11-16
This may sound crazy, but try installing Linux first. After installing Windows, there's a way to edit Windows' boot loader so that Linux can boot after Windows is installed. It's online somewhere. I don't remember more than that.

---

### Post by ramjet_1953 on 2007-11-16
The answer to this is the same as reading the stories in Aviation Review, where air crashes are analyzed. Something like 99.9% of aviation accidents are caused through "Pilot Error".

Exactly the same situation occurs when installing Linux in a dual boot situation.

Many people dive in without doing the necessary homework and then blame Linux for their own mistakes.

A few things that are a "MUST DO".

1. Defragment your Windows hard drive two or three times before doing anything else.

2. Back up your important data.

3. Did I mention to back up your important data?

4. Use the gparted live CD to re-size your existing Windows partition.

5. Make sure you really know what you are doing. Don't try to do it with the book in one hand and typing in commands with the other.

6. If you don't do it "by the numbers", don't come onto this forum, winging that Ubuntu destroyed your important data.

Regards,
Roger :cool:

---

### Post by tlg on 2007-11-26
Well the problem of Windows failing to start in a dual boot situation with Ubuntu on IBM/Lenovo T41 Laptops is resolved here:

[https://bugs.launchpad.net/ubuntu/+bug/25451](https://bugs.launchpad.net/ubuntu/+bug/25451) 

It is due to the existence of a reserved portion of the disc set up by the original IBM installation process. This area is used for utilities which can be accessed prior to the OS startup by a special "Access IBM" button.

This feature can be disabled in the Security section of the bios and voila everything is back to normal. 

Apparently Windows gets confused about the state of the partition table when Ubuntu installs after Windows and the special IBM part of the disc is enabled.

So it seems it is still a bug in the Ubuntu install process because all is OK until Ubuntu and Grub loader are installed,but at least there is a workaround.

Interestingly I have a Dell Laptop with a similar disc arrangement for playing DVDs etc without booting the OS, and it works OK with dual boot. However I have seen reports that using this facility can 'corrupt' the partition table and break the boot process.

 So it seems it is not an entirely simple matter.

---

