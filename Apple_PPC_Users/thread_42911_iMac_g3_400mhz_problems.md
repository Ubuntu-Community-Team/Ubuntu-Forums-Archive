---
title: "iMac g3 400mhz problems"
date: 2005-06-19
forum: Apple PPC Users
---

### Post by mooseman on 2005-06-19
Hi, 
For the past two days I have been attempting to get Ubuntu running on my iMac g3, but unsuccessfully.  I'm fairly new to the world of linux and would appreciate some help.  My first error during the installation occurred after detection of hardware, something along the lines of failure of configuring a mutliseat system (no idea what it means), so I figured heck, I might as well skip it.  Everything ran smoothly until the installation of the yaboot boot loader, in which it failed to install.  A little background, I was attempting to install this on my 10gb internal HD, and the bootstrap partition appeared to be created.  I also started the installation after completely reformatting the HD after failed gentoo endeavors :-P.  I have osx booting from my 80 gb external hd.  I would appreciate help as this is giving me a ridiculous headache!
Edit: On my first attempt i figured i could skip the installation of the yaboot boot loader, and attempt a manual boot? To me it appeared that when attempting to boot my system it was somehow calling a non existant gentoo kernel? So lost!

---

### Post by diebels on 2005-06-19
Doing:
"sudo dd if=/dev/zero of=/dev/hda bs=512 count=1"
from a live cd or something would get rid of the gentoo bootloader.

---

### Post by DJ_Max on 2005-06-20
I have the same system. I got the same error during the install. Also, skipping the Yaboot loader was a bad thing, because without it, your computer won't boot correctly.

A Multi-seat setup is having multiple workplaces, card, screen+keyboad+mouse in one PC.

---

### Post by Len on 2005-06-21
[QUOTE=diebels]Doing:
"sudo dd if=/dev/zero of=/dev/hda bs=512 count=1"
from a live cd or something would get rid of the gentoo bootloader.[/QUOTE]

Err... this command is very dangerous unless you want to wipe the whole drive, or are you sure it doesn't overwrite the partition map? /dev/hda*x* where *x* is your yaboot partition would be the right path for dd. It then writes 512 zero bytes to that partition in this case, instead of to the drive...

With the Yaboot errors I cannot help much, I have had some problems with it as well... You can try to configure Yaboot manually from the CD if it is supported there (if not, mount the HFS yaboot partition and edit). Holding 'alt' when booting your mac (only on the iMac II or later) will allow you to select Yaboot (hopefully) in case it doesn't start automatically (assuming Yaboot is properly installed), on older machines, or if 'alt' doesn't list yaboot, you'll have to use an Open Firmware command like ```
boot hd:*x*,yaboot
``` where *x* is the partition number where Yaboot resides (use fdisk or Mac OS X pdisk, partition is "Apple Bootstrap" and very small, can't miss it). You can access the OF by pressing apple+alt+o+f when powering your mac.

---

### Post by hackersmovie on 2008-03-21
really old thread, I know. I also am trying to install Ubuntu 7.04 on my iMac G3 (now has a G4/400 CPU) I can boot the live CD using " live-nosplash-powerpc " I can run the live CD all day, I can go through the entire installer no issues or errors. When I click "restart" to actually use the OS, it never completely shuts down or restarts. So, I unplug the power, restart and the yaboot (version 1.3.13) hangs at " Please wait, loading kernel. . . " 

Any ideas?

---

### Post by stream303 on 2008-03-21
I'd definitely try the "alternate" installer version that is text-graphics based, and not a live cd desktop.  Are you dual-booting the old mac-os, or are you letting guided partitioning use the "whole disk" rather than just free space?

Which version of Mac is it and how much ram does it have?  Have any components been upgraded or swapped?  This site is handy for finding some specs:

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Keep these faqs handy:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
and
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Looking forward to seeing that iMac up and running!

---

### Post by hackersmovie on 2008-03-21
> **stream303 said:**
> I'd definitely try the "alternate" installer version that is text-graphics based, and not a live cd desktop.  Are you dual-booting the old mac-os, or are you letting guided partitioning use the "whole disk" rather than just free space?

Which version of Mac is it and how much ram does it have?  Have any components been upgraded or swapped?  This site is handy for finding some specs:

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Keep these faqs handy:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
and
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Looking forward to seeing that iMac up and running!

I'll try the alternate version.

I'm not dual booting, just want Ubuntu on this machine. 

I've tried the guided partitioning, I've done it manually to use the whole disk. I made 3 partitions:
1 = New world - 1MB
2 = ext3 (mount point / ) formatted
3 = swap - 1578MB

My iMac is a G3 Rev. A "Bondi Blue". I've upgraded the CPU to a G4/400 Mhz. I've added 4MB VRAM, 80GB Seagate 7200RPM HD, 512MB RAM,

---

### Post by hackersmovie on 2008-03-21
o.k. so here's where I'm at: (basically same place I was before)

I used Xubuntu 6.06 Alternate 

"Select and Install Software" failed

I proceeded with install

When it reboots I get this: (same as with Ubuntu Live CD 7.04)

```
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot: linux
Please wait, loading kernel  . . .
/pci@800000000/mac-io@10/ide@20000/disk@0:3,/boot/vm l inux: Input/output error
boot:
Please wait, loading kernel. . . 
```

Now, I've tried installing these versions:
Xubuntu 6.06 Alternate
Xubuntu 7.04 Alternate
Ubuntu 6.06 Live CD
Ubuntu 7.04 Live CD
Kubuntu 6.06 Live CD
Xubuntu 6.06 Live CD

I've used Guided Partitioning, I've partitioned manually, I've done the installs with and without internet connections, I've tried installing with OS X intalled, without OS X installed, with the drive formatted for OSX but nothing installed, the drive formatted as "free space", with multiple blank partitions.

I'm at my wits end here. At best I can get it installed (I think) and when it reboots I get the message above. . . 

What am I missing here? The machine specs are above in my previous post.

Thanks in advance for any insight!

---

### Post by stream303 on 2008-03-21
> **hackersmovie said:**
> My iMac is a G3 Rev. A "Bondi Blue". I've upgraded the CPU to a G4/400 Mhz. I've added 4MB VRAM, 80GB Seagate 7200RPM HD, 512MB RAM,

There's the problem.  There is an 8gb limit on that machine, so when you partition, make it no larger than 7.5 gb to be safe.

If you are skilled at manually partitioning, you could manually slice and dice it up with seperate /usr /home /var etc on the disk, but be sure to keep Ubuntu itself no larger than 7.5 gb.

You could try upgrading the firmware, but for now I'd just do a quick test at 7.5 gb max to see how you like the machine..

The easiest way to go about it now, would be to use manual partitioning to delete the existing partitions, then use the *go-back* feature to do a guided partitioning with a max of 7.5 gb..

---

### Post by hackersmovie on 2008-03-21
> **stream303 said:**
> There's the problem.  There is an 8gb limit on that machine, so when you partition, make it no larger than 7.5 gb to be safe.

If you are skilled at manually partitioning, you could manually slice and dice it up with seperate /usr /home /var etc on the disk, but be sure to keep Ubuntu itself no larger than 7.5 gb.

You could try upgrading the firmware, but for now I'd just do a quick test at 7.5 gb max to see how you like the machine..

The easiest way to go about it now, would be to use manual partitioning to delete the existing partitions, then use the *go-back* feature to do a guided partitioning with a max of 7.5 gb..

EXCELLENT! Thanks! I'm doing it now. Just a note: 

I think I'm fairly proficient at partitioning, here's what I did:

Deleted all partitions

hda1 = newworld 1MB
hda2 = ext3 7000MB (formatted as / )
hda3 = swap 512MB

the balance I left as free space, if it works and boots, I'll reinstall and set up /media, etc.

Does this all sound right? 

Thanks so much for your responses, it's given me new hope for Linux!

---

### Post by hackersmovie on 2008-03-21
That was it! Thanks so much! I'm doing the updates now. One question. . . 

I'll use it as is for now just to poke around. I'll want to be able to use the balance of the HD though. When I reinstall, and do the partitions again, what should I partition the balance as just so it will mount on the desktop? I just want to use it for pics, audio, etc.

Thanks again!

---

### Post by Cows on 2008-03-21
Make sure you don't forget to use the rest of the space.

---

### Post by slacka-vt on 2008-03-21
> **hackersmovie said:**
> That was it! Thanks so much! I'm doing the updates now. One question. . . 

I'll use it as is for now just to poke around. I'll want to be able to use the balance of the HD though. When I reinstall, and do the partitions again, what should I partition the balance as just so it will mount on the desktop? I just want to use it for pics, audio, etc.

Thanks again!

If you want to install Mac OS X on the free space,
partition it as "Free Space" or "Unused".
If I remember correctly, HFS and HFS+ are not options.
If they are, use them.
When Mac detects an unformatted partition, it "should" ask you
If you want to "initialize" the volume.

If you want to use the space for storage accessed by your Linux install, you should format it as ext2 (or ext3).
Either file system will be accessible.

~s

---

### Post by oswaldkelso on 2008-03-23
> **slacka-vt said:**
> If you want to install Mac OS X on the free space,
partition it as "Free Space" or "Unused".
If I remember correctly, HFS and HFS+ are not options.
If they are, use them.
When Mac detects an unformatted partition, it "should" ask you
If you want to "initialize" the volume.

If you want to use the space for storage accessed by your Linux install, you should format it as ext2 (or ext3).
Either file system will be accessible.

~s

On the rev A the 8gb limit is a hardware limit that applies to osx and linux. If your going to dual boot linux and osx **BOTH ** osx and linux must be on that first 8gb. Also its much easier to put osx on first and linux second as osx will over write your yaboot settings. In reality it also means that you may as well use the mac osx install disk to do your partitioning

---

