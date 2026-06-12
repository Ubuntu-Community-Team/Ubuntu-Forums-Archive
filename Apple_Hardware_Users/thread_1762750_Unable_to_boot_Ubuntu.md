---
title: "Unable to boot Ubuntu"
date: 2011-05-19
forum: Apple Hardware Users
---

### Post by danradu on 2011-05-19
Hi guys,

I installed Ubuntu 10.04LTS 64bit on a MacBook Pro 5,4 with OS X 10.6.7 - Dual-Boot - folowing the instructions at :
[https://help.ubuntu.com/community/Ma...stall%20Ubuntu]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#You%20have%20already%20installed%20Mac%20OSX%20and%20Windows%20Vista,%20now%20to%20install%20Ubuntu").

When trying to boot Ubuntu I get this : "Non-system disk. Press any key..."
Pressing any key does not reboot. Have to power off/on.

Can't figure out what went wrong.... help please.

---

### Post by avtolle on 2011-05-19
Have you read [http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677) ?

---

### Post by danradu on 2011-05-19
> **avtolle said:**
> Have you read [http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677) ?
Yes, I did.
rEFIt did not find anything wrong tochange. The partitions were in sync.
Do I need to install grub ?
I thought it gets installed in the Linux partition during the 'Advanced' option of the last step of the Ubuntu install.

---

### Post by danradu on 2011-05-19
This is the partition info from Mac's Partition Inspector :

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    430097143  Mac OS X HFS+
 3      430097144    608349419  Basic Data
 4      608349420    625137344  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    430097143  af  Mac OS X HFS+
 3      430097144    608349419  83  Linux
 4      608349420    625137344  82  Linux swap / Solaris

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 430097144:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 608349420:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris


Looks like Grub is installed in my Linux partition (/dev/sda3).
I try now to boot using the 'alt' key - no rEFIt installed.
I get 2 options 'Mac' and 'Windows'.
If I select 'Windows' I get a black screen with a blinking cursor.

Anybody seeing something wrong ?

---

### Post by jamesjenner on 2011-05-20
Ahh I didn't look at this post because I thought it was regarding an existing install.

I had the exact same problem as you. It's caused by not using gParted from LiveCD before installing Ubuntu. If you use the partitioning tool in the install process it causes the exact same problem as your experiencing.  

Funnily enough someone else has the exact same problem, which I just replied to.

The solution is to reinstall, make sure you use gParted as per the sticky (i know the sticky is for a diff version but it's okay). When you boot up to LiveCD make certain you run gParted from the LiveCD and create the partitions you need as per the sticky. When your in the install step, just choose the partitions or set their type. Do not repartition via it, for some unknown reason that seems to cause the problem (well it did in my case).

Btw, FYI I have a MacBook 5,1 and installed Ubuntu 11.04. Only thing I've had to do extra is install the multi touch drivers that is in another thread in this subforum. Other than that, it's very nice!

---

### Post by danradu on 2011-05-20
> **jamesjenner said:**
> Ahh I didn't look at this post because I thought it was regarding an existing install.

I had the exact same problem as you. It's caused by not using gParted from LiveCD before installing Ubuntu. If you use the partitioning tool in the install process it causes the exact same problem as your experiencing.  

Funnily enough someone else has the exact same problem, which I just replied to.

The solution is to reinstall, make sure you use gParted as per the sticky (i know the sticky is for a diff version but it's okay). When you boot up to LiveCD make certain you run gParted from the LiveCD and create the partitions you need as per the sticky. When your in the install step, just choose the partitions or set their type. Do not repartition via it, for some unknown reason that seems to cause the problem (well it did in my case).

Btw, FYI I have a MacBook 5,1 and installed Ubuntu 11.04. Only thing I've had to do extra is install the multi touch drivers that is in another thread in this subforum. Other than that, it's very nice!

Thanks for the reply.
Giving me some hope ...
Can you point me to the exact sticky you are referring to ?
I did use GParted from the LiveCD before starting the installer. Coming from OS X I only had a 'Free Space' after the Mac partition. I used GParted to create the ext4 Linux partition (/dev/sda3) followed by the Linux swap partition (/dev/sda4). Then I started the install.
During the install I selected the manual process and 'Changed' the /dev/sd3 partition to be the ext4filesystem and to mount it at '/'. In the final step I selected 'Advanced' and told it to install the boot loader to /dev/sda3.

Did I miss something ?

---

### Post by jamesjenner on 2011-05-20
> **danradu said:**
> Thanks for the reply.
Giving me some hope ...
Can you point me to the exact sticky you are referring to ?
I did use GParted from the LiveCD before starting the installer. Coming from OS X I only had a 'Free Space' after the Mac partition. I used GParted to create the ext4 Linux partition (/dev/sda3) followed by the Linux swap partition (/dev/sda4). Then I started the install.
During the install I selected the manual process and 'Changed' the /dev/sd3 partition to be the ext4filesystem and to mount it at '/'. In the final step I selected 'Advanced' and told it to install the boot loader to /dev/sda3.

Did I miss something ?

Ahh my mistake, I had a look at the sticky and it wasn't what I used even though I thought it was. What I used was the installation support wiki link from the FAQ sticky. My bad sorry.

Well the link is:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I followed the section titled "Dual-Boot: Mac OSX and Ubuntu" and followed the detailed instructions. 

I noticed some really bizzar behavoir from the partition tool in the installation software, I would keep getting 0 sized partitions. At one stage I figured out that by deleting/creating partitions I would get an extra 0 sized partition and I suspect it's this behaviour that causes the problems. 

I wish now I had documented exactly what I did, but at the time I was just trying to get it to work. I do know that I resized the partitions via the OSX utility, I booted up the live CD, I used gParted to setup the paritions as per the above link and then I started the installation. I chose to install and do network updates including the closed source drivers (was only for sound from memory) and then when it came to disk I chose manual, set the partitions in terms of what they are (main to mount as /, etc) doing the bare minimum as possible and told Grub (though it doesn't call it grub) to load into the same drive as the Linux partition (which I think you did as well).

After that it installed for ages, rebooted and I saw the Tux in the rEFIt loader which was a beautiful site :)

Good luck.

---

### Post by danradu on 2011-05-20
> **jamesjenner said:**
> Ahh my mistake, I had a look at the sticky and it wasn't what I used even though I thought it was. What I used was the installation support wiki link from the FAQ sticky. My bad sorry.

Well the link is:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I followed the section titled "Dual-Boot: Mac OSX and Ubuntu" and followed the detailed instructions. 

I noticed some really bizzar behavoir from the partition tool in the installation software, I would keep getting 0 sized partitions. At one stage I figured out that by deleting/creating partitions I would get an extra 0 sized partition and I suspect it's this behaviour that causes the problems. 

I wish now I had documented exactly what I did, but at the time I was just trying to get it to work. I do know that I resized the partitions via the OSX utility, I booted up the live CD, I used gParted to setup the paritions as per the above link and then I started the installation. I chose to install and do network updates including the closed source drivers (was only for sound from memory) and then when it came to disk I chose manual, set the partitions in terms of what they are (main to mount as /, etc) doing the bare minimum as possible and told Grub (though it doesn't call it grub) to load into the same drive as the Linux partition (which I think you did as well).

After that it installed for ages, rebooted and I saw the Tux in the rEFIt loader which was a beautiful site :)

Good luck.

Now I am really puzzled.
That is the link I used as an installation guide and the very same section Dual-Boot ...
Didn't notice anything abnormal during the partition creation or after.

Now here is something interesting : I tried installing Ubuntu 11 64bit over the same partitions  (re-formatting the /dev/sda3 obviously). Went through the same steps as with the 10.04 version and selected to install the boot loader into /dev/sda3.
Installer run smoothly to the end. I reboot and this time the rEFIt gpartsync found the GPT out of sync with MBR. Resync, reboot and I end up again with the blinking cursor.
However this time the OS X Partition Inspector gives me a slightly different output :

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    430097143  Mac OS X HFS+
 3      430097144    608349419  Basic Data
 4      608349420    625137344  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    430097143  af  Mac OS X HFS+
 3 *    430097144    608349419  83  Linux
 4      608349420    625137344  82  Linux swap / Solaris

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 430097144:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 608349420:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris


Identical with the previous one except that now the 'Boot Code' for the Linux partition is 'None'.
Before I had :
MBR contents: Boot Code: GRUB  + Partition at LBA 430097144: Boot Code: GRUB

Now :
MBR contents: Boot Code: GRUB  + Partition at LBA 430097144: Boot Code: None

What is the meaning of the MBR : Boot Code : GRUB  ?
Shouldn't the Partition at LBA 430097144 (my Linux) also have Boot Code : GRUB ?

I'm totally confused.:o

Thanks

---

### Post by jamesjenner on 2011-05-20
The default for where GRUB installs is the device. In my case I had to change it to the correct option and not the default. I presume you would have been in the same boat. Other than that I'm not sure. Even though it was about a week ago when I did this, I cannot remember 100% what I did during the install step, I thought I changed the type and where it is mounted (Linux for / and Swap was all) but I don't think I chose to reformat it. Again not 100% sure.

Going into Disk Utility it's telling me I have:

[LIST=1]
[*]EFI, 210 MB, Partition Type: EFI System Partition, Partition Flags: -, Type FAT (32-bit)
[*]Macintosh HD 34 GB, Partition Type: Apple HFS/HFS+ Partition, Partition Flags -, Type HFS+
[*]SWAP, Partition Type: Linux Swap Partition, Partition Flags -
[*]216 GB ext4, Partition Type: Linux Basic Data Protection, Partition Flags: -, Type: Ext4 (version 1.0)
[/LIST]
I do remember the first time I tried it I put the SWAP second but the second time I made SWAP before the Linux partition.

Can't remember anything else that could be different.

:edit:

just rebooted the lappy and did the same as you, here's the report:
```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     67256359  Mac OS X HFS+
 3       67258368     69306367  Linux Swap
 4       69306368    488396799  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     67256359  af  Mac OS X HFS+
 3       67258368     69306367  82  Linux swap / Solaris
 4 *     69306368    488396799  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 67258368:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 69306368:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active
```

Yeah your right, second time around for you looks worse not better. And I've noticed that yes, you have put the swap second (which to me seems natural, but hey the wiki says to put it second and it worked for me, maybe just coincidence).  Mine is closer to your original one than the later one other than the swap position.

---

### Post by danradu on 2011-05-21
> **jamesjenner said:**
> The default for where GRUB installs is the device. In my case I had to change it to the correct option and not the default. I presume you would have been in the same boat. Other than that I'm not sure. Even though it was about a week ago when I did this, I cannot remember 100% what I did during the install step, I thought I changed the type and where it is mounted (Linux for / and Swap was all) but I don't think I chose to reformat it. Again not 100% sure.

Going into Disk Utility it's telling me I have:

[LIST=1]
[*]EFI, 210 MB, Partition Type: EFI System Partition, Partition Flags: -, Type FAT (32-bit)
[*]Macintosh HD 34 GB, Partition Type: Apple HFS/HFS+ Partition, Partition Flags -, Type HFS+
[*]SWAP, Partition Type: Linux Swap Partition, Partition Flags -
[*]216 GB ext4, Partition Type: Linux Basic Data Protection, Partition Flags: -, Type: Ext4 (version 1.0)
[/LIST]
I do remember the first time I tried it I put the SWAP second but the second time I made SWAP before the Linux partition.

Can't remember anything else that could be different.

:edit:

just rebooted the lappy and did the same as you, here's the report:
```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     67256359  Mac OS X HFS+
 3       67258368     69306367  Linux Swap
 4       69306368    488396799  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     67256359  af  Mac OS X HFS+
 3       67258368     69306367  82  Linux swap / Solaris
 4 *     69306368    488396799  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 67258368:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 69306368:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active
```Yeah your right, second time around for you looks worse not better. And I've noticed that yes, you have put the swap second (which to me seems natural, but hey the wiki says to put it second and it worked for me, maybe just coincidence).  Mine is closer to your original one than the later one other than the swap position.


Installed one more time Ubuntu 11 over the existing partitions - the exact same steps as during the previous install. This time I end up with the exact same partition info as when installing Ubuntu 10.04 (MBR contents: Boot Code: GRUB  + Partition at LBA 430097144: Boot Code: GRUB). Still can't get it to boot.

As you say during the  install the default for the boot loader is /dev/sda but I set it to /dev/sda3 (my ext4 partition). I guess that's the right way.

I am still not clear what does the 'MBR contents: Boot Code: GRUB' mean ?

One other thing : 
When I was missing the 'MBR contents: Boot Code: GRUB' part rEFIt was still giving me 2 options : 'Mac OS X' and 'Linux HD'. 
When the 'Partition at LBA 430097144: Boot Code: GRUB' shows up rEFIt gives me 3 options : 'Mac OS', 'Linux HD' and 'Linux from partition 3'. 
Looks like something is wrong. The 'Linux HD' option seems to be bogus and I can never get rid of it.
Even when I manage to get the more meaningful 'Linux from partition 3' it is still ineffective.

Looks like something is corrupt in the main partition (since that is the one that never gets modified) and prevents the boot loader to either get installed or run from the Linux partition.

---

### Post by jamesjenner on 2011-05-21
> **danradu said:**
> Installed one more time Ubuntu 11 over the existing partitions - the exact same steps as during the previous install. This time I end up with the exact same partition info as when installing Ubuntu 10.04 (MBR contents: Boot Code: GRUB  + Partition at LBA 430097144: Boot Code: GRUB). Still can't get it to boot.

Bugger mate, did you still have SWAP after your Linux or move your Linux to after SWAP, from what I can tell that's the only thing different between yours and mine right now.

> **danradu said:**
> As you say during the  install the default for the boot loader is /dev/sda but I set it to /dev/sda3 (my ext4 partition). I guess that's the right way.

Yes, that's what I did and it appeared to work for me. I presume that is why I have the Boot Code: GRUB.

> **danradu said:**
> I am still not clear what does the 'MBR contents: Boot Code: GRUB' mean ?

Only using an educated guess (without knowing that much about macs) I think it refers to whether the partition can be booted or not and if so what type of boot it is. Which to me makes sense but may be totally off base.

> **danradu said:**
> One other thing : 
When I was missing the 'MBR contents: Boot Code: GRUB' part rEFIt was still giving me 2 options : 'Mac OS X' and 'Linux HD'. 
When the 'Partition at LBA 430097144: Boot Code: GRUB' shows up rEFIt gives me 3 options : 'Mac OS', 'Linux HD' and 'Linux from partition 3'. 
Looks like something is wrong. The 'Linux HD' option seems to be bogus and I can never get rid of it.
Even when I manage to get the more meaningful 'Linux from partition 3' it is still ineffective.

Looks like something is corrupt in the main partition (since that is the one that never gets modified) and prevents the boot loader to either get installed or run from the Linux partition.

Possibly, though I think it's more to do with rEFTIt than whatever is on the OSX partition, I wouldn't have thought that it would touch OSX at all when booting. Again, only guessing, don't take me as an authority on this.

I would say as a couple of last options you could try:

[LIST=1]
[*]Reinstall but use gParted to make swap sda3 and linux sda4, ie do SWAP first not second.
[*]Install as only Linux
[/LIST]
The last one I reckon only do as a last resort. From what I've read you only really need OSX to install firmware updates but there is a way to do it without OSX (not sure why I would need firmware updates, everything for me is ok but I thought meh, costs me only a small amount of disk space).

Good luck.

---

### Post by danradu on 2011-05-21
Believe it or not, I did try the Linux-swap followed by Linux layout first. I thought reversing it might make a difference. No luck. It fails as bad in both cases.

I'll try asking some questions on a Mac forum. I need to understand what's the deal with the MBR boot code and why does rEFIt gives me the option to boot 'Linux HD' even without installing Ubuntu.

Thanks a bunch for the feedback.

---

### Post by srs5694 on 2011-05-21
I don't have a simple solution, but I can provide some information that may help get you working, eventually....

First, you've got a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) on your disk, which is an ugly and dangerous hack that Apple uses (in conjunction with BIOS emulation in the EFI) to get Windows to dual-boot with OS X on Macs. This isn't really necessary with Linux, since Linux can boot from EFI and understands GPT natively. I've got [a Web page](http://www.rodsbooks.com/ubuntu-efi/index.html) on how to boot Ubuntu on Macs using EFI/GPT mode; however, my personal experience in this respect is limited to a 1st-generation Mac Mini, which is different in significant ways from a MacBook Pro 5,4. Also, there's been [a report of EFI-booting a Mac damaging its firmware.](http://ubuntuforums.org/showthread.php?t=1743664) You'll have to judge for yourself whether it's worth the risk to try it. I'm afraid I don't understand the cause well enough to offer an opinion of how likely it is you'd run into this problem yourself.

The usual way to create a hybrid MBR generates MBR entries for the first three GPT partitions on the disk, excluding the EFI System Partition. This can have implications if the OS requires MBR support or if any boot loader in the chain uses the MBR. Linux ignores the MBR on hybrid disks, so MBR entries for Linux don't matter unless there's a boot loader issue.

I haven't studied this in detail, but rEFIt seems to probe for bootable code in several ways: It looks for .efi files (EFI boot loaders) in the EFI System Partition; it looks for boot code in the MBR; and I believe it also looks for boot code in at least some partitions' boot sectors. Thus, you can see options appear and disappear as you modify each of these things. I don't know if rEFIt handles partitions that are in the MBR any differently from those that aren't. If it does, moving a partition in or out of the hybrid MBR could affect whether it appears in the rEFIt menu.

On a non-Mac PC with UEFI, I've recently discovered that ELILO is much more reliable than GRUB 2 in booting Ubuntu. OTOH, I've had no luck with ELILO on my 32-bit Mac Mini. It might be worth installing and trying ELILO, though.

I'm not familiar with Mac's Partition Inspector, but it sounds like the "Boot Code: GRUB" lines are reporting that the utility has detected GRUB executable code in the partition. This is what you'd find if you installed the BIOS version of GRUB in the relevant MBR or partition boot sector.

In my own EFI installations, it hasn't seemed to matter where I tell the installer to install GRUB from the selector button (/dev/sda or a Linux partition such as /dev/sda3 or whatever); however, these have been installations in native EFI mode. In theory, installing to the MBR vs. the Linux partition shouldn't matter when installing in BIOS mode in terms of OS X's ability to handle the installation. As noted earlier, though, I don't know what rEFIt would pick up.

---

### Post by jamesjenner on 2011-05-21
> **danradu said:**
> Believe it or not, I did try the Linux-swap followed by Linux layout first. I thought reversing it might make a difference. No luck. It fails as bad in both cases.

I'll try asking some questions on a Mac forum. I need to understand what's the deal with the MBR boot code and why does rEFIt gives me the option to boot 'Linux HD' even without installing Ubuntu.

Thanks a bunch for the feedback.

No worries, just sorry I couldn't help with your problem. Let us know how you progress with your problems. I have to admit your situation is a tad odd. There's always the option of installing OSX on a flash drive and making your hard disk only linux, or forgo OSX all together, but that to me is not the best way to go, depending on your circumstances.

Good luck!

---

### Post by danradu on 2011-05-21
> **jamesjenner said:**
> No worries, just sorry I couldn't help with your problem. Let us know how you progress with your problems. I have to admit your situation is a tad odd. There's always the option of installing OSX on a flash drive and making your hard disk only linux, or forgo OSX all together, but that to me is not the best way to go, depending on your circumstances.

Good luck!

I asked a few questions on the mac-forums.com site and someone confirmed that the GRUB in the MBR indicates the MBR is corrupt.
Having established that, I booted a Windows XP CD (happened to have one on hand), went into the 'Recovery Console' by pressing 'R' (make sure you don't press 'ENTER' or you'll wipe out the OS X partition) and run 'fixmbr' at the windows prompt.
Re-booted and now I am staring at the Ubuntu login ... Bliss

---

### Post by jamesjenner on 2011-05-21
> **danradu said:**
> I asked a few questions on the mac-forums.com site and someone confirmed that the GRUB in the MBR indicates the MBR is corrupt.
Having established that, I booted a Windows XP CD (happened to have one on hand), went into the 'Recovery Console' by pressing 'R' (make sure you don't press 'ENTER' or you'll wipe out the OS X partition) and run 'fixmbr' at the windows prompt.
Re-booted and now I am staring at the Ubuntu login ... Bliss

Ahh congratulations, I'm glad it's working for you. 

I'm kinda confused as to where the corruption is. I thought MAC's used EFI and this is in it's own special parition. Where is the MBR and why was the windows recovery console able to repair it? 

Cheers,

James.

:edit:

oh, don't forget to make the thread as [SOLVED], you can do it via the thread tools. Will help people if they're searching with the same problem :)

---

### Post by srs5694 on 2011-05-22
> **jamesjenner said:**
> I'm kinda confused as to where the corruption is. I thought MAC's used EFI and this is in it's own special parition. Where is the MBR and why was the windows recovery console able to repair it?

You're confusing several different things:


[LIST]
[*]**Firmware type**
[LIST]
[*]**BIOS** -- This is the firmware used on most commodity PCs. It's been around for just shy of 30 years now. Intel-based Macs also include a BIOS emulation mode, although they aren't really BIOS-based (see next point).
[*]**EFI** -- This is the firmware used on Macs and some other computers (Itanium-based computers and some commodity PCs). It supports entirely new ways of booting and other features not present in the antiquated BIOS.
[/LIST]
 
[*]Partition table type
[LIST]
[*]**MBR** -- This is the old style of partition table. It supports up to four *primary* partitions, one of which can be an *extended* partition that can hold an arbitrary number of *logical* partitions. Windows can only boot from MBR disks when booted using BIOS firmware (or BIOS emulation in EFI). The MBR primary partition table is stored on sector 0 of the disk, which is also known as the MBR and also holds boot loader code (see below).
[*]**GPT** -- This is a newer partition table type with fewer limitations than MBR. Of particular interest for this discussion, GPT includes a "protective MBR," which is a valid MBR data structure that defines a partition that spans the entire disk. Its purpose is to keep GPT-unaware utilities from messing with the disk; it should *not* be accessed like other MBR partitions. When used on a UEFI-based computer, 64-bit versions of Windows Vista and 7 boot from GPT; however, the Mac's EFI is too old for Microsoft to support, so on a Mac, BIOS emulation (and MBR) must be used.
[/LIST]
 
[*]**Boot loader code** -- On a BIOS-based computer, the first boot loader code to be executed when the computer boots is stored in the first sector of the disk (the MBR). This code can be the DOS/Windows boot loader, part of GRUB, or various other things. Apparently the original problem was caused by GRUB overwriting the DOS/Windows boot loader code (although that's a bit puzzling to me, since AFAIK it should still have worked that way).
[/LIST]

---

### Post by danradu on 2011-05-22
> **jamesjenner said:**
> Ahh congratulations, I'm glad it's working for you. 

I'm kinda confused as to where the corruption is. I thought MAC's used EFI and this is in it's own special parition. Where is the MBR and why was the windows recovery console able to repair it? 

Cheers,

James.

:edit:

oh, don't forget to make the thread as [SOLVED], you can do it via the thread tools. Will help people if they're searching with the same problem :)

The partition table layout on intel-based Macs is GPT. The GPT space is allocated in the first 40 logical blocks (LBA0 - LBA39). Then comes the EFI system, then the HFS+, etc...
By definition, the GPT hosts at LBA0 the 'Legacy MBR' (512 bytes0.
The first 446 bytes in the MBR are supposed to contain code used to boot the machine.
The remaining 66 bytes include signature info and the primary partitions table.
If the GRUB gets written over the code area of the MBR and possibly overflows in the signature area the firmware might not recognize the GPT as valid and refuse to boot it.

Since the GPT 'Legacy MBR' is at LBA0 it is treated as a standard MBR by BIOS based firmware. That's why Windows XP can properly manipulate it.

If there is a lesson to learn from all this is that on intel-based Macs :
1. an MBR having GRUB on it is a sure sign of corruption
2. it can be easily fixed with help from Windows XP via the 'fixmbr' command

The counter intuitive part here is that you can use Windows to fix a problem created by a different OS. :)

Cheers,
Dan

---

### Post by jamesjenner on 2011-05-22
> **srs5694 said:**
> You're confusing several different things:


[LIST]
[*]**Firmware type**
[LIST]
[*]**BIOS** -- This is the firmware used on most commodity PCs. It's been around for just shy of 30 years now. Intel-based Macs also include a BIOS emulation mode, although they aren't really BIOS-based (see next point).
[*]**EFI** -- This is the firmware used on Macs and some other computers (Itanium-based computers and some commodity PCs). It supports entirely new ways of booting and other features not present in the antiquated BIOS.
[/LIST]
 
[*]Partition table type
[LIST]
[*]**MBR** -- This is the old style of partition table. It supports up to four *primary* partitions, one of which can be an *extended* partition that can hold an arbitrary number of *logical* partitions. Windows can only boot from MBR disks when booted using BIOS firmware (or BIOS emulation in EFI). The MBR primary partition table is stored on sector 0 of the disk, which is also known as the MBR and also holds boot loader code (see below).
[*]**GPT** -- This is a newer partition table type with fewer limitations than MBR. Of particular interest for this discussion, GPT includes a "protective MBR," which is a valid MBR data structure that defines a partition that spans the entire disk. Its purpose is to keep GPT-unaware utilities from messing with the disk; it should *not* be accessed like other MBR partitions. When used on a UEFI-based computer, 64-bit versions of Windows Vista and 7 boot from GPT; however, the Mac's EFI is too old for Microsoft to support, so on a Mac, BIOS emulation (and MBR) must be used.
[/LIST]
 
[*]**Boot loader code** -- On a BIOS-based computer, the first boot loader code to be executed when the computer boots is stored in the first sector of the disk (the MBR). This code can be the DOS/Windows boot loader, part of GRUB, or various other things. Apparently the original problem was caused by GRUB overwriting the DOS/Windows boot loader code (although that's a bit puzzling to me, since AFAIK it should still have worked that way).
[/LIST]


I understand about BIOS but I'm not familiar with MBR. I'm also not famialr with EFI and only discovered it recently due to the Mac issues. I think the thing that was confusing me is that on my MacBook it has a partition called EFI that is 210MB so I presumed it is an actual partition on the HD. Disk Utility in Ubuntu (11.04) states the type as being FAT, with the partition type being EFI System Partition. Am I correct in saying this is a partition on the HDD? And if so then how does this correlate to your description of EFI? If it's firmware why is there a partition for it? 

as you say, I'm kinda :confused: but more so because of the partition labelled EFI.

---

### Post by srs5694 on 2011-05-22
> **jamesjenner said:**
> I understand about BIOS but I'm not familiar with MBR. I'm also not famialr with EFI and only discovered it recently due to the Mac issues. I think the thing that was confusing me is that on my MacBook it has a partition called EFI that is 210MB so I presumed it is an actual partition on the HD. Disk Utility in Ubuntu (11.04) states the type as being FAT, with the partition type being EFI System Partition. Am I correct in saying this is a partition on the HDD? And if so then how does this correlate to your description of EFI? If it's firmware why is there a partition for it?

EFI is a (relatively) new firmware system that's slowly working its way into the marketplace. Itanium servers, Intel-based Macs, and a small but growing number of commodity PCs use EFI. Among other things, EFI includes a specification for a partition for its own use, known as the EFI System Partition (ESP). This partition should have a FAT filesystem and a particular type code GUID. The ESP is *used by* the EFI, but it is not itself the EFI, any more than a refrigerator thermometer is a refrigerator. Specifically, the ESP can hold OS-specific boot loaders (so no more messing with boot loader code in the disk's boot sector), drivers for hardware so that the EFI can use it, and some other things. Note that the ESP on a Mac can be empty, but it's at least supposed to exist.

This is further complicated by the fact that, although Intel-based Macs are natively EFI-based, their EFIs include a BIOS compatibility layer to enable them to dual-boot with Windows. This layer is typically used with a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is a hybridization of GPT and MBR that mostly works but is extremely dangerous.

Note also that partition names can be confusing because there's no standardization for names, so different utilities can give the same partition different names; and sometimes partitions intended for different purposes have similar names. For instance, the protective partition in the MBR of GPT disks was called the "EFI GPT" partition until a few months ago; now it's called simply "GPT". This partition is unrelated to the ESP, but Mac users with hybrid MBRs often think they're one and the same because they often occupy a similar (but not quite identical) set of disk sectors. GPT provides a name field, so you can give any partition any name you like (encoded in Unicode and up to a certain size), but this name has no effect on how an OS treats the partition. GNU Parted identifies the ESP by giving it a "boot flag". GPT fdisk (gdisk) identifies it by giving it a type code of EF00. Sorry if this is confusing; as I say, the confusion derives from the fact that nobody in authority has bothered to clearly specify partition type names, although the type code numbers are (relatively) clearly specified.

---

### Post by srs5694 on 2011-05-22
> **danradu said:**
> The partition table layout on intel-based Macs is GPT. The GPT space is allocated in the first 40 logical blocks (LBA0 - LBA39).

Actually, with a default configuration, GPT data occupies the first 34 512-byte sectors (LBA 0 to 33). Apple starts its first partition at sector 40 for reasons I don't know, although I'd speculate that it's to keep the partition properly aligned on Advanced Format disks, which require alignment on 8-sector multiples for optimum performance.

> By definition, the GPT hosts at LBA0 the 'Legacy MBR' (512 bytes0.
The first 446 bytes in the MBR are supposed to contain code used to boot the machine.
The remaining 66 bytes include signature info and the primary partitions table.

This is mostly correct, but I'd like to make a few corrections:


[list]
[*]The EFI specification refers to the MBR of a GPT disk as a "protective MBR;" the term "legacy MBR" generally refers to the MBR of a disk using the MBR partitioning system and *not* using GPT. I don't mean to be nit-picking, but the terminology surrounding all this stuff is confusing enough without trying to correctly interpret mistaken uses.
[*]The first 440 bytes, not 446, are unambiguously reserved for boot code. The next 4 bytes are a disk signature and the next 2 bytes are normally null (0) values. That said, some boot loaders apparently use 446 bytes for boot code, although I don't know precisely which ones do this.
[*]EFI-based systems do *not* use the MBR's boot code; they use a boot loader that's built into the EFI itself, typically in conjunction with files in the EFI System Partition (ESP), although the Mac's EFI can load code from a Mac's OS installation partition. A Mac that dual-boots with Windows, or often with Linux, employs a BIOS compatibility feature that makes it work like a BIOS-based computer when booting an OS in this mode, and in this case the boot code in the MBR may be used.
[*]To be clear, the final 66 bytes of the MBR consist of four partition table entries (16 bytes each) followed by an MBR signature (which is distinct from the disk signature; the disk signature is a sort of serial number, whereas the MBR signature is a two-byte code that identifies the partition as having valid MBR data).
[/list]


> If the GRUB gets written over the code area of the MBR and possibly overflows in the signature area the firmware might not recognize the GPT as valid and refuse to boot it.

Overwriting the first 446 bytes of the MBR on a GPT disk will have no effect on the correct identification of the disk or on OS X's ability to boot; however, this might affect the ability of OSes that use BIOS mode to boot.

If the final 66 bytes of the MBR are overwritten or damaged, the proper identification of the disk as GPT disk may be impaired. This type of damage is easily repaired with the right tools, though; provided the damage is limited to the MBR, the most important GPT data structures will be unaffected, so creating a new protective MBR will fix the disk.

> Since the GPT 'Legacy MBR' is at LBA0 it is treated as a standard MBR by BIOS based firmware. That's why Windows XP can properly manipulate it.

Although Windows XP can (relatively) safely modify the boot loader portion of a protective MBR, it is neither safe nor proper for Windows XP to manipulate the partition table of a protective MBR. A GPT disk's "real" partitions are defined in GPT data structures outside of the MBR, and any attempt by XP to adjust partition table entries in the MBR could create an extremely dangerous mismatch. There are two broad cases:

On a 100% legal and valid GPT disk, the protective MBR's partition table contains precisely one entry: a type-0xEE partition that spans the entire disk (or up to 2 TiB, on disks larger than this). With the exception of some rare 64-bit versions or if you've added a third-party GPT driver, Windows XP can't handle GPT disks, and so shouldn't be messing with the disk at all. If you want XP to use the disk, you've got to do something else with it....

Apple uses the ugly and dangerous [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration to enable OS X and Windows to dual-boot on Macs. This setup is a standards-violating hack that involves shrinking the protective MBR's 0xEE partition and adding up to three duplicates of valid GPT partitions to the MBR. This enables Windows to see and install to a GPT disk (or at least, up to three of its partitions), but Windows should not be modifying those partitions or adding new ones because doing so would modify the MBR partition but not its GPT counterparts. This could leave the partitions in a highly dangerous out-of-sync condition, which would likely result in trashed filesystems and lost files. A partial exception to this is that Windows may safely modify the partition type codes and boot flags in the MBR; but any attempt by any MBR-only utility to modify the start point or size of any partition will almost certainly create problems.

> If there is a lesson to learn from all this is that on intel-based Macs :
1. an MBR having GRUB on it is a sure sign of corruption

Not necessarily. GRUB is a boot loader, just like any other. If you use BIOS mode to install Linux, then GRUB can be installed to the MBR and might work fine. I've done this, although I prefer to boot in a pure EFI/GPT environment on my Mac Mini, so it's not currently configured in this way.

For more information, please read:


[list]
[*][The Wikipedia article on GPT](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[*][The Wikipedia article on MBR](http://en.wikipedia.org/wiki/Master_boot_record)
[*][My Web page on hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid[/url)
[*][Apple's Tech Note 2166](http://developer.apple.com/library/mac/#technotes/tn2166/_index.html)
[*][Intel's EFI specifications](http://www.intel.com/technology/efi/main_specification.htm) or [the UEFI 2.x specifications](http://www.uefi.org/specs/) (both pages have links that require you to accept terms and conditions to download the specs as PDF files)
[/list]

---

### Post by jamesjenner on 2011-05-22
> **srs5694 said:**
> For more information, please read:


[LIST]
[*][The Wikipedia article on GPT]("http://en.wikipedia.org/wiki/GUID_Partition_Table")
[*][The Wikipedia article on MBR]("http://en.wikipedia.org/wiki/Master_boot_record")
[*][My Web page on hybrid MBRs]("http://www.rodsbooks.com/gdisk/hybrid[/url")
[*][Apple's Tech Note 2166]("http://developer.apple.com/library/mac/#technotes/tn2166/_index.html")
[*][Intel's EFI specifications]("http://www.intel.com/technology/efi/main_specification.htm") or [the UEFI 2.x specifications]("http://www.uefi.org/specs/") (both pages have links that require you to accept terms and conditions to download the specs as PDF files)
[/LIST]


Thanks for your explanation, it's been really helpful. I'm still a bit vague on some details but it's starting to make sense and the links will help a lot! It's good to get a handle on these things so as to better assist others ;) I don't personally plan to buy any more macs, but who knows what the future holds?

---

### Post by srs5694 on 2011-05-22
> **jamesjenner said:**
> I don't personally plan to buy any more macs, but who knows what the future holds?

Since PCs are shifting to UEFI firmware, many of the issues that affect Macs will soon affect a large number of PC users. Some, though, won't -- Windows installs in UEFI mode on such computers rather than requiring an ugly and dangerous hack, so multi-boot configurations will be much saner on UEFI-based PCs.

---

