---
title: "Gparted on Ubuntu does not see my upgraded MacBook Hard Drive [HELP]"
date: 2007-09-06
forum: Apple Intel Users
---

### Post by undead-monkey on 2007-09-06
Here is my issue:

I recently upgraded my Core Duo BlackBook from its original 80Gb drive, to a 160Gb version.
Ubuntu had been installed on the 80 Gb, and I was going to do a fresh dual boot install on the 160Gb with Fiesty and OSX.
Live CD works fine, however Gparted does not see my HD or any of the partitions on it.
Then I tried with a clean freshly formated HD (to see if maybe boot camp, or my OSX partition were the culprit) still no dice.

On my 80Gb drive, I had run Dapper, Edgy, and then Fiesty with no issues.

I am assuming this may be a hardware issue with the drive and Linux (Windows, and OSX all install fine on it) but I am hoping someone here might have an answer for me so I can get Ubuntu up and running again and stop using Parallels all day.

Thanks in advance.

---

### Post by undead-monkey on 2007-09-07
Hate to do this, but...

bump.

---

### Post by benanzo on 2007-09-07
You might try doing:
```
sudo fdisk -l
```
in a terminal while booted in the LiveCD just to make sure that it's not actually just a problem with parted/gparted.  I have a 160 GB Hitachi Deskstar drive in my first-gen MacBook and I've never had any problems.

---

### Post by undead-monkey on 2007-09-08
I'll give that a try this weekend.

---

### Post by undead-monkey on 2007-09-08
> **benanzo said:**
> You might try doing:
```
sudo fdisk -l
```
in a terminal while booted in the LiveCD just to make sure that it's not actually just a problem with parted/gparted.  I have a 160 GB Hitachi Deskstar drive in my first-gen MacBook and I've never had any problems.


Tried fdisk, but got absolutely nothing. No readout at all.

I had thought it might have been a problem with the MBR after a I had run BootCamp again, but there doesn't seem to be an issue there either.

Ubuntu just won't show, or mount my hard drive.

I'm as lost as ever.

---

### Post by cyberdork33 on 2007-09-09
Seems very odd, like a kernel module is not loaded or something... can you give output of lsmod.

EDIT: You might try booting the gutsy live cd too, see if you get different results since it uses a later kernel.

---

### Post by undead-monkey on 2007-09-10
I haven't tried Gutsy, but I did attempt with Edgy and Dapper to see if it had just been my live cd.

I am wondering if it has something to do with the Samsung (I think it was samsung at least) 160gb I installed. Could it just be incompatible hardware? I haven't had any issues under OSX.

---

### Post by macboontu on 2007-09-10
I've tried with Gusty LiveCD, but nothing changes.

I installed a 160gb Samsung too! Is an incompatibility hardware problem possible? How is it possible?

---

### Post by pxwpxw on 2007-09-10
I suggest run these if you can and post results.
Just to see if all the partitioning  looks ok first.
 
From macosx
```

 diskutil list

```

The  rEFIt menu Partition utility (gptsync) - list the GPT and MBR tables.

---

### Post by cyberdork33 on 2007-09-10
> **macboontu said:**
> I've tried with Gusty LiveCD, but nothing changes.

I installed a 160gb Samsung too! Is an incompatibility hardware problem possible? How is it possible?

It is possible... some kind of new firmware that isn't recognized. It seems HIGHLY unlikely though, most of this stuff is very standardized.

---

### Post by macboontu on 2007-09-10
```
$ diskutil list
/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *149.1 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS OSX                15.0 GB   disk0s2
   3:   Microsoft Basic Data                    133.7 GB  disk0s3

```

I've tried all kind of test. In my first installation (on original 80gb hard disk) I had no problem!
So you think there is an incompatibility between MacBook and Samsung hard disk? However OSX works perfectly!

In this case the only solution is to wait an Apple firmware upgrade?

---

### Post by cyberdork33 on 2007-09-10
> **macboontu said:**
>  In this case the only solution is to wait an Apple firmware upgrade?
I was referring to the drive's firmware. Nothing to do with Apple (Unless like Apple OEM drives has Apple firmware on it.) If it can be found what the root issue is, then it is probably a kernel code fix... at least from what i have seen so far... You guys probably should file a bug.

---

### Post by undead-monkey on 2007-10-02
bump

---

### Post by ronocdh on 2007-10-06
> **undead-monkey said:**
> bump
There was an Apple EFI update less than a week ago. This did not affect the issue?

---

### Post by undead-monkey on 2007-10-06
I'll give that a try. 
I saw the update on the Apple support site, but was assuming it was for Core 2Duo Macs only.

---

### Post by undead-monkey on 2007-10-06
The EFI update was not for my machine. 
It was for C2D MacBooks.
Still not luck on Linux recognizing my HD.

---

### Post by undead-monkey on 2007-10-27
Finally figured out the issue.

I did a clean install of OSX on my MacBook (which brought it back down to 10.4.6) and gparted saw my disk just fine. I than did the OSX system updates and brought it up to date and ran the live CD again, and it was a no go.

Conclusion:
You need to be running an earlier version of OSX in order for Ubuntu to see the partitions.

I never would have thought that it was Apple software causing the problem.

---

### Post by macboontu on 2007-11-06
Hey, great news!

But I originally did a 10.4.6 OSX intallation, and gparted does not saw the hard disk.... 

What's wrong?

---

### Post by undead-monkey on 2007-11-06
Ok, back to the drawing board then....

BTW:
I am now running Leopard and continue to have the same issue.
Guess it is just the HD.

---

### Post by macboontu on 2007-11-06
Uhm, I was in doubt about my previous installations (if I updated OSX or not), so i did a new one. But nothing changes.

Can you show me in details which steps you've done to get your hard disk detected?

---

### Post by evil-nick on 2007-11-07
Could it be a bootcamp issue?  I'm having the same problems...  I had Ubuntu on my Macbook (1st-Gen) with a 60G drive, ditched it for lack of space, and when I installed my 160G drive I got Fedora Core 6 beta installed, but when Fedora final came out it wouldn't see the drive to upgrade over it, even though the beta was still there and still worked.

I then tried Ubuntu, a couple other distros I had, and even XP, none would find it.  I finally gave up, did a reinstall, then XP installed fine, and works fine.  I tried to install over it with Gutsy today, and it doesn't work...  I think I'm going to d-load a Gentoo disk and try that...  OSX is nice and all... but I miss my Linux (I've actually been using my desktop more since I graduated school just because it has Linux ;))

---

### Post by evil-nick on 2007-11-07
I don't know if anyone can make sense of this, but dmesg shows this from when I booth the 7.10 LiveCD:

libata version 2.21 loaded.
[    3.036000] ata_piix 0000:00:1f.1: version 2.11
[    3.036000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    3.036000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.040000] scsi0 : ata_piix
[    3.052000] usbcore: registered new device driver usb
[    3.092000] scsi1 : ata_piix
[    3.092000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000120c0 irq 14
[    3.092000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x000120c8 irq 15
[    3.100000] USB Universal Host Controller Interface driver v3.0
[    3.500000] Clocksource tsc unstable (delta = -395071436 ns)
[    3.664000] ata1.00: ATAPI: MATSHITACD-RW  CW-8221, GA0J, max UDMA/33
[    3.836000] ata1.00: configured for UDMA/33
[    4.004000] scsi 0:0:0:0: CD-ROM            MATSHITA CD-RW  CW-8221   GA0J PQ: 0 ANSI: 5
[    4.004000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    4.004000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    4.160000] PCI: Enabling device 0000:00:1f.2 (0005 -> 0007)
[    4.160000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    4.160000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.160000] scsi2 : ata_piix
[    4.160000] scsi3 : ata_piix
[    4.160000] ata3: SATA max UDMA/133 cmd 0x000120d8 ctl 0x000120fe bmdma 0x00012020 irq 19
[    4.160000] ata4: SATA max UDMA/133 cmd 0x000120d0 ctl 0x000120fa bmdma 0x00012028 irq 19


According to the system info within Ubuntu, ata_piix is the driver that should be used... I also found it referenced as the driver for building the kernel on Gentoo for the Macbook Pro...  The Gentoo livecd also says 

ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
ata_piix 0000:00:1f.2: invalid MAP value 0

at boot... anyone know if that, or any of this is relevant?

The closest I got was using a scsi driver from within the text-based installer, and then it only found the 8M bootloader partition that XP uses...

---

### Post by macboontu on 2007-11-09
I don't think it's a bootcamp issue, but I don't understand what it could be.

Alas, I'm considering to purchase another disk.... :(

---

### Post by cyberdork33 on 2007-11-09
> **macboontu said:**
> I don't think it's a bootcamp issue, but I don't understand what it could be.

Alas, I'm considering to purchase another disk.... :(
Just from the information I have seen so far, I would say there is a bug in one of the kernel modules. ata_piix maybe? Has anyone actually filed a bug report on this yet?

---

### Post by evil-nick on 2007-11-09
I don't think I have a Samsung drive, I think I have a Hitachi...  I'll check today after work.  I don't think it's a kernel issue because of my history..

Installed 160G drive, dual boot OSX Fedora 7 Beta.
Ran Fedora Core 7 Final to upgrade, could not find drive.
Ubuntu 6.10 Could not find drive.
Ubuntu 7.04 could not find drive.
Windows XP could not find drive.
Reinstall OSX, re-bootcamp it, XP installs fine.
XP runs fine now (just as Fedora 7 Beta did), but installers/livecd can't find drive.

Prolly should submit a bug-report ;)

---

### Post by evil-nick on 2007-11-09
It's actually a Wester Digital (I should have known that, I installed it myself).  Does anyone know if other distro's users have found a solution?  If it works in another distro, we can fix it in this one.  I want my Linux back!

---

### Post by macat on 2007-11-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/158166](https://bugs.launchpad.net/ubuntu/+bug/158166) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello!

[https://bugs.launchpad.net/ubuntu/+bug/158166](https://bugs.launchpad.net/ubuntu/+bug/158166)

Also I have this problem. I neeeed help, because I've tried everything, and I don't find the soultion.

The Ubuntu 6.06 see the disk, and the partitions.

---

### Post by evil-nick on 2007-11-09
How's this for dirty:  Install ubuntu 6.06, then upgarde all the way to Gutsy? ;)

Vector Linux can see it from the command line using fdisk, but complains that all the partitions have different physical/logical beginnings and endings, not do they end on a cylinder boundary, whatever that means...  I'm going to try 6.06 now...

---

### Post by cyberdork33 on 2007-11-09
> **evil-nick said:**
> How's this for dirty:  Install ubuntu 6.06, then upgarde all the way to Gutsy? ;)

Vector Linux can see it from the command line using fdisk, but complains that all the partitions have different physical/logical beginnings and endings, not do they end on a cylinder boundary, whatever that means...  I'm going to try 6.06 now...

That means it is not reading the partitions correctly either.

Alright, if people are willing to total start from scratch, can you make it completely free space on the disk, and try to run the Ubuntu LiveCD?

Try formatting it with MSDOS partition format in Disk Utility (instead of GPT). (Note OSX will not install unless it is GPT).

---

### Post by macat on 2007-11-10
You wrote, "Note OSX will not install unless it is GPT".
Last Week I tried:
(From [Launchpad]("https://bugs.launchpad.net/ubuntu/+bug/158166"))
"First:
  1. Knoppix in
  2. Delete all partition
  3. Create 3 partition: 1. ntfs(because the osx saw this), 2. linuxswap, 3. ext3
  4. Reboot, Ubuntu in
  5. Huhuu... The Ubuntu saw the disk. I installed the Ubuntu(7.10) rapidly. Fine. Reboot.
  6. The OSX didn't want to the Knoppix's partition table. I didn't understand it. So... The OSX don't install after the Ubuntu. Ohh... Not fine..."

The Ubuntu 6.06 has problems, and I need the new features.

---

### Post by cyberdork33 on 2007-11-10
> **macat said:**
> 6. The OSX didn't want to the Knoppix's partition table. I didn't understand it. So... The OSX don't install after the Ubuntu. Ohh... Not fine..."
The OSX installer checks that the disk is partitioned in a GPT format. It will only continue if it is formatted in this way. gParted supports writing a GPT format so make that you note this when using gParted to do partitioning. fdisk does NOT support GPT so it will not allow an install.

However, OSX can RUN on a non-GPT disk. You just have to use a trick to get it on there.

[http://ubuntuforums.org/showpost.php?p=3186229&postcount=10](http://ubuntuforums.org/showpost.php?p=3186229&postcount=10)

---

### Post by macat on 2007-11-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/158166](https://bugs.launchpad.net/ubuntu/+bug/158166) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hooooooray!

I accomplished the task...but this is not the final solution.

The Way:

 1. Boot with Knoppix
 2. With GParted delete all partition, and create: 1 swap, 1 ext3, 1 ntfs
 3. Install Ubuntu to ext3 partition
 4. Plugin the old drive to USB (with Sata -> USB Converter, external drive)
 5. Boot old OSX system from the old drive... it is slow, because USB isn't very fast...
 6. With Apple's Disk Utility, format the 3rd partition to hfs+
 7. With Carbon Copy Cloner clone the system into the new partition
 8. Reboot, unplug the old drive, and the Refit is working without intervention

OK, but I don't have EFI partition, so I lose the firmware upgrade chance.

---

### Post by evil-nick on 2007-11-12
I don't have my old drive anymore, I traded it in for a discount on my 160G...

---

### Post by macboontu on 2007-11-13
Hey guys, here my (simple) solution:

1. Boot with OSX dvd
2. Format entire disk with FAT fs using OSX Disk Utility
3. Reboot with Ubuntu Live CD, and install it
4. Reboot and admire GRUB starting up Ubuntu

I don't know if will be possible to install OSX at this point, but it seem possible if you leave enough space and format it with OSX Disk Utiliy. Anyway, I'm happy with my new Gusty Linux and I'm not interested in OSX yet :)

---

### Post by cyberdork33 on 2007-11-13
> **macboontu said:**
> Hey guys, here my (simple) solution:

1. Boot with OSX dvd
2. Format entire disk with FAT fs using OSX Disk Utility
3. Reboot with Ubuntu Live CD, and install it
4. Reboot and admire GRUB starting up Ubuntu

I don't know if will be possible to install OSX at this point, but it seem possible if you leave enough space and format it with OSX Disk Utiliy. Anyway, I'm happy with my new Gusty Linux and I'm not interested in OSX yet :)
You need to partition for OSX if you want it, otherwise this should be fine.

---

