---
title: "Am I the only one using a B&amp;W? Boot failure...pls help!"
date: 2008-11-07
forum: Apple Hardware Users
---

### Post by hopefulone on 2008-11-07
I don't know what else to try at this point. I have a B&W (Yosemite) rev. A with an Acard 6260M pci-ide card since the onboard controllers have a history of corruption. I have three drives attached: hde - ubuntu (100gb), hdf - data ((music, etc) 120gb), hdh - mac os x (100gb). 

This config works great from os x and from live cd for gutsy and hardy. I have been able to use and install from live cd's without error. I have also tried alternate cds for Hardy and Intrepid. Both install without issue or error. 

The problem rears its ugly head when I boot (post-install). I have updated yaboot.conf with nosplash so I can see when the boot process stops. This reveals that for all three attempts (7.10, 8.04.1 & 8.10) boot proceeds normally until the partition scan/check (?) which results in repeated lost interrupts and ultimately boot failure. What makes this so frustrating is that watching the boot process from live cd (nosplash) or alternate install cd, the system just skims right through with no delay or issue. 

By boot failure I mean it never proceeds past the repeated lost interrupt / DMA recovery messages for each hard drive. It seems to eventually catch partition data and disk size, etc. from each volume but cannot seem to reconcile this info since it has taken so long to receive. I even tried leaving it overnight since some posts said "it just took awhile". Nope. 

I have opened a bug at [http://bugzilla.kernel.org/show_bug.cgi?id=11943](http://bugzilla.kernel.org/show_bug.cgi?id=11943) on the advice received from my only other post. After an initial response from the tracker team to try a different kernel, it seems my request to them for guidance in that effort has fallen on deaf ears. I understand that it is not their job to hold my hand but I have never had a response of any kind since that time. Huh.?.

I am more than happy to try a different kernel but don't know how to do that from live cd or alt install cd. I attempted to compile a new kernel but live cd ran out of memory and failed. It doesn't seem that the live cd makes use of the swap partition created during install or at least it is only using 390mb of it...not enough to install necessary components, source and compile. Then when I tried to save the kernel source to one of my disks, I did not have write access permissions from the live cd. Ouch!

I have read uncountable threads trying to find a solution to this problem. I have tried noapic, nodma, irqpoll, etc in the yaboot.conf append line. I have reviewed lsmod from live cd and compared it to lsmod from alternate cd to the install (from initramfs prompt) to determine if some module is not loading at boot that is required and tried updating-initramfs with various module configurations to no avail. 

This is an aging machine which works okay (i.e. no problems) in os x 10.4.11 but I would like to try linux to see if I can give it a new life. So far, I am extremely disappointed in the results and am about to give up. 

Does anyone have any ideas or been successful themselves? Ubuntu really appealed to me when I tried the Hardy live cd the first time. I don't know what else to try at this point. 

Please help if you can. Thank you.

---

### Post by tiresia on 2008-11-07
I'm not sure, that I can help you, because I don't know this card.
After a short search, I found that there was a similar problem - but only with old kernel (2.4.x)
In one post is suggested to run a ROM upgrade, *before* installing linux 
(and you should it from OS9)
Here is are two links with a similar problem (from OpenSuse and from Debian)
[http://lists.opensuse.org/opensuse-ppc/2002-04/msg00013.html](http://lists.opensuse.org/opensuse-ppc/2002-04/msg00013.html)
[http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg30686.html](http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg30686.html) 
And here is the link, where you can find the ROM upgrade
[http://www.acard.com.tw/english/fc0101.jsp#](http://www.acard.com.tw/english/fc0101.jsp#)
::::::::
If you want to work 'inside' your installed system, starting from a LiveCD,
you should use 'chroot' - is the same process Gentoo uses to install (you can mount swap partition, install and configure your kernel, &#8230;). If you are interested, you can read some Gentoo-docs (of course there are also some good ones from Debian, but I found Gentoo documentation at the same easy and complete)
[http://www.gentoo.org/doc/en/handbook/index.xml](http://www.gentoo.org/doc/en/handbook/index.xml)

---

### Post by stream303 on 2008-11-07
I'm having a similar issue with Intrepid, although I'm running a G5 iMac with an external firewire drive - which I can usually bend to my will post-install with no problems, but not this time.  The improvements to yaboot are great, but I'm suspecting that the UUID's in the /etc/fstab are wrong once rebooted normally.

I haven't had a lot of time to experiment, so later this week I'm going to install just the server and do a lot of comparisons, checking the uuid's with

```
sudo blkid
```

etc.

In the meantime, how about a band-aid?  If there is some confusion post-install, I'm wondering how your install would go if you temporarily disconnected your two other drives, and tried to install to your dedicated 100gb Ubuntu drive with the others temporarily disconnected?

I'm hoping to do more testing later, so If I come up with anything, you'll be the first to know...

Don't give up, I'm sure there's quite a few of us dealing with the same scenario...

---

### Post by hopefulone on 2008-11-07
Tiresia, thank you for the links and guidance. I decided to bite the bullet and reinstall OS 9 to check the firmware on the 6260M. It was not up to date after all. I had only applied version 3.12 years ago but had been SO sure I had applied all the firmware updates available for all my components <sheepish grin>. 

By applying that firmware update and using the "irqpoll" option at boot the system now reads the disks and sees the partitions. Unfortunately the boot process is still stalling due to lost interrupt / DMA recovery messages from all three disks. I tried noapic, nolapic, noacpi, acpi=off, pci=noacpi, acpi=noirq but no further progress yet. 

You definitely got me further along than I was before! Thanks again. I will keep trying...

---

### Post by hopefulone on 2008-11-07
> **stream303 said:**
> I'm having a similar issue with Intrepid, although I'm running a G5 iMac with an external firewire drive - which I can usually bend to my will post-install with no problems, but not this time.  The improvements to yaboot are great, but I'm suspecting that the UUID's in the /etc/fstab are wrong once rebooted normally.

I haven't had a lot of time to experiment, so later this week I'm going to install just the server and do a lot of comparisons, checking the uuid's with

```
sudo blkid
```

etc.

In the meantime, how about a band-aid?  If there is some confusion post-install, I'm wondering how your install would go if you temporarily disconnected your two other drives, and tried to install to your dedicated 100gb Ubuntu drive with the others temporarily disconnected?

I'm hoping to do more testing later, so If I come up with anything, you'll be the first to know...

Don't give up, I'm sure there's quite a few of us dealing with the same scenario...

Thanks for the ideas! I did apply a 4 year old firmware update to the 6260M and with irqpoll get further in the boot process. At least now the system sees all the partitions and can read the cylinder and block data. I am still seeing lost interrupts / DMA recovery preventing boot completion but making a little progress!

---

### Post by tiresia on 2008-11-08
Can you please post your /etc/fstab (from the installed system)?

---

### Post by hopefulone on 2008-11-08
> **tiresia said:**
> Can you please post your /etc/fstab (from the installed system)?

Here it is: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde3
UUID=c86029ea-9f72-447d-b4a3-f48da87a7b33 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hde4
UUID=3f388197-8548-485b-a064-74f6b21ce6d8 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by hopefulone on 2008-11-08
> **hopefulone said:**
> Here it is: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde3
UUID=c86029ea-9f72-447d-b4a3-f48da87a7b33 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hde4
UUID=3f388197-8548-485b-a064-74f6b21ce6d8 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Here is the output of blkid, in case it helps: 
```
ubuntu@ubuntu:~$ sudo blkid
/dev/hde2: TYPE="hfs" 
/dev/hde3: UUID="c86029ea-9f72-447d-b4a3-f48da87a7b33" TYPE="ext3" 
/dev/hde4: UUID="3f388197-8548-485b-a064-74f6b21ce6d8" TYPE="swap" 
/dev/hdf9: TYPE="hfsplus" 
/dev/hdf10: TYPE="hfsplus" 
/dev/hdh3: TYPE="hfsplus" 
/dev/loop0: TYPE="squashfs" 
```

---

### Post by tiresia on 2008-11-08
Reading the links I mentioned yesterday (in opersuse and in debian), it seems that the IDE-Card simulates actually a SCSI Card (because of a problem with Open Firmware). And it seems that MacOS9 sees the Card as SCSI-Card (can you please check this in OS9?). 
So - most probably I'm wrong!!! - I thought, maybe the Installer sees the Card correctly as IDE, but when the kernel start from the partition doesn't see any IDE-Card (because it gets information from the OpenFirmware)?!? :confused: :( :confused:

If you see in the fstab the Installer detected it as IDE card (therefore hde) - but is the kernel detecting it as scsi???

It probably totally absurd, :shock: but can you please make a try.
Start from the LiveCD, and make a backup of your fstab file
```
sudo cp /etc/fstab /etc/fstab.bak
```
Edit the file just changing 'hde3' with 'sde3' (or maybe 'sdb3' :shock: - because it is seen as a second scsi ???)
If it does not work, resume your fstab
```
sudo cp /etc/fstab.bak /etc/fstab
```

---

### Post by stream303 on 2008-11-08
Makes me wonder if going into a virtual terminal and doing

```
modprobe ide-core
```

might help?  Admittedly I'm kind of lost here, but have seen this pop up in earlier releases once in awhile...

---

### Post by hopefulone on 2008-11-09
> **tiresia said:**
> Reading the links I mentioned yesterday (in opersuse and in debian), it seems that the IDE-Card simulates actually a SCSI Card (because of a problem with Open Firmware). And it seems that MacOS9 sees the Card as SCSI-Card (can you please check this in OS9?). 
So - most probably I'm wrong!!! - I thought, maybe the Installer sees the Card correctly as IDE, but when the kernel start from the partition doesn't see any IDE-Card (because it gets information from the OpenFirmware)?!? :confused: :( :confused:

If you see in the fstab the Installer detected it as IDE card (therefore hde) - but is the kernel detecting it as scsi???

It probably totally absurd, :shock: but can you please make a try.
Start from the LiveCD, and make a backup of your fstab file
```
sudo cp /etc/fstab /etc/fstab.bak
```
Edit the file just changing 'hde3' with 'sde3' (or maybe 'sdb3' :shock: - because it is seen as a second scsi ???)
If it does not work, resume your fstab
```
sudo cp /etc/fstab.bak /etc/fstab
```

Well, it was worth a shot but unfortunately with set as sde3 I encountered a white screen and after alt-F2 saw a hang at partition check. Set as sb3 did not have white screen hang but still hde:lost interrupt hang. I tried both settings with and without irqpoll. 

Kernel Bug Tracker responded and seems to think that:
[I]It could be that AEC6260[R] controllers may need the same quirks (i.e.
explicitly enabling IRQ line output) as AEC6280[R] ones on Macintosh (draft
patch for 2.6.28-rc3 attached to the next comment). 
[/I]
I have absolutely no idea what to to with the patch and am not even sure if it is intended for me or is internal for them...

---

### Post by hopefulone on 2008-11-09
> **stream303 said:**
> Makes me wonder if going into a virtual terminal and doing

```
modprobe ide-core
```

might help?  Admittedly I'm kind of lost here, but have seen this pop up in earlier releases once in awhile...

Thank you for the suggestion. Unfortunately I had tried modprobe ide-core and the system responded that "module does not exist". :(

---

### Post by tiresia on 2008-11-09
Have you tried to switch the HD's connection with the CD-ROM's?
Maybe it just the easiest solution

---

### Post by hopefulone on 2008-11-09
> **tiresia said:**
> Have you tried to switch the HD's connection with the CD-ROM's?
Maybe it just the easiest solution

Hmm. I still need to dual boot with Mac OS X. Will this work? What about the other two drives attached to the ide card?

---

### Post by tiresia on 2008-11-09
I don't know, it was just an idea, to see if your problem depends on that ide-card.
How many drives are attached? Can't you attach the CD-ROM to the IDE Card together with the MacOS Drive? Can you please check if it is true what I was telling two days ago, that MacOS sees the Card as a SCSI Card?

---

### Post by hopefulone on 2008-11-09
And it could be the answer...I might give it a try but not today. My concern is that if I need to boot from CD (holding down C key at startup) in Linux or Mac OS X for repair, etc. it may not find the CDROM correctly when not connected to its dedicated port (am I crazy on that one?). It might just do the trick though.  

I have three drives attached to the ACARD all jumpered to cable select. hde(master)-Ubuntu, hdf(slave)-Mac music, movies, picts, etc. hdh(slave)-Mac OS X 

Mac OS X does see the card as SCSI through emulation, confirmed via System Profiler.

PS - thanks for hanging in and helping try to solve this puzzle. I truly appreciate the efforts! It is still very curious to me that Live CD and Alternate CD both boot and run without a problem but the installed system won't...Meh. :)

---

### Post by tiresia on 2008-11-09
> **hopefulone said:**
> And it could be the answer...I might give it a try but not today. My concern is that if I need to boot from CD (holding down C key at startup) in Linux or Mac OS X for repair, etc. it may not find the CDROM correctly when not connected to its dedicated port (am I crazy on that one?). It might just do the trick though.  

Of course if the CD-ROM should not work, it is not a good situation. Most probably you need to zap the PRAM (cmd+opt+P+R) at bootup. 

> **hopefulone said:**
> 
Mac OS X does see the card as SCSI through emulation, confirmed via System Profiler.
That confirms what I said before. We should also try to understand how the OpenFirmware sees it. I bet as SCSI

> **hopefulone said:**
> 
PS - thanks for hanging in and helping try to solve this puzzle. I truly appreciate the efforts! It is still very curious to me that Live CD and Alternate CD both boot and run without a problem but the installed system won't...Meh. :)
That it's exactly the point. When you will switch CD-ROM and HD, try to boot from the CD-ROM with the Linux Installer and with a MAC-Installer (to be sure that you can boot). If the Mac-Installer boots, but the Ubuntu-Installer can't, it means that the Linux-Kernel can see the Card but can't boot from a Drive attached to it. 
If the Linux Installer boots, it means that there is something wrong with the Installation (or only with the Installed-kernel).
:::::
When you know more about it, you can try to boot the Installer from an USB-memory Stick. Or try to compile a different Kernel (it depends how much time you want to spend to solve this problem)

---

