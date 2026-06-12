---
title: "How to install Ubuntu without a CD (Macbook Air 3,2)"
date: 2010-10-29
forum: Apple Hardware Users
---

### Post by apoth on 2010-10-29
How can I install Ubuntu on a MBA?

I've tried creating USB flash disks and disk partitions but I can't set them as the startup disk in OSX's preferences.

It claims not to even be able to read the disks. I can verify on a separate Linux desktop that at least the USB flash disk is readable and I strongly suspect the partition I tried dd'ing the iso to is fine too. Thanks in advance for any suggestions.

---

### Post by SuperDodge on 2010-10-29
Use ReFit

---

### Post by apoth on 2010-10-29
Thanks. I've got it installed but it doesn't seem to see the USB flash drive?

---

### Post by apoth on 2010-10-29
I have two other partitions than OSX - one large ready for Ubuntu, one smaller one with the iso dd'd onto it.

Refit gives me the OSX icon and a legacy hard disk diamond icon - which leads to just the text 'missing operating system' being shown.

---

### Post by apoth on 2010-10-30
So, I've tried using an external USB hard disk to boot from and refit actually gives me a Tux icon now - but choosing it still just says:

```
missing operating system
```

Any suggestions? Thanks.

---

### Post by apoth on 2010-10-30
Why is this so difficult?

---

### Post by linuxopjemac on 2010-10-30
maybe this helps:
[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=88](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=88)
[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick)

---

### Post by apoth on 2010-10-30
Thanks - they offered a slightly different approach, installing rEFIt on the USB disk instead of the computer.

All I got out of it though was a different way to reach the missing operating system error. :(

Is that actually a grub error? I would have expected grub to show me a menu to pick a boot choice from before it got to a missing operating system error?

---

### Post by apoth on 2010-10-31
Does anyone have any idea if it's likely that I'm doing something wrong?

If I buy an external CD/DVD drive will that make any difference? If it could does it have to be a particular drive? Obviously I don't really want to buy more hardware if I'm going to be stuck in the same situation but if that's what it takes...

---

### Post by linuxopjemac on 2010-10-31
What you could try is to make three partitions from the OSX installation disk. One for OSX and one for Ubuntu (and one for swap later). Create a bootable USB stick with Ubuntu on it (test it on another computer). Then dd that stick to the second partition, like some other guy did:

> I just got one of the new MacBook Airs today and I'm trying to install Ubuntu. I've installed refit, resized the Mac Partition, created two new partitions, used dd to image a bootable USB to one of the new partitions and I'm able to boot off of it.

When booting into Ubuntu, the screen is off-center with vertical colored bars that roll on the screen. Has anyone figured out how to get around this yet?
see [http://ubuntuforums.org/showthread.php?t=1603365](http://ubuntuforums.org/showthread.php?t=1603365)

---

### Post by apoth on 2010-10-31
Thanks. That does clearly imply it's possible, it's something I've already tried without success.

This is my disk at the moment:

```
$ diskutil list/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *121.3 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            50.6 GB    disk0s2
   3:                  Apple_HFS                         14.4 GB    disk0s3
```

So I've tried, for instance:

```
$ sudo dd if=Downloads/ubuntu-10.10-desktop-amd64.iso of=/dev/disk0s3 bs=1m
```

I've tried not specifying the blocksize, I've tried instructions for converting the iso to a dmg and using that instead of the iso, I've tried using Ubuntu on another machine to create a USB startup disk and then specifying that as /dev/disk1 for the input file argument to dd.

I must be missing something?

---

### Post by linuxopjemac on 2010-10-31
Ask they guy who did it initially, he must know what he has done. Maybe he dd-ed some working Ubuntu disk onto a partition, instead of an installation CD.

---

### Post by SuperDodge on 2010-10-31
I'm the one who has it working.  Don't dd an iso.  Make a bootable usb stick and boot off of it on another computer to ensure it works.  Then dd the disk itself (/dev/disk1, etc) to the partition you made on the internal SSD.

It works and it's not difficult at all.  Good luck!

---

### Post by apoth on 2010-10-31
Thanks. I got marginally different results this time, an extra line of output:

```
Missing operating system
No bootable device -- insert boot disk and press any key
```

What I did was create a USB disk using Ubuntu's startup disk creator on another machine from the 10.10 64bit iso.

Then I dd'd the USB disk to the partition using:

```
sudo dd if=/dev/disk1 of=/dev/disk0s3 bs=1m
```

But obviously, it's still not working for me. :(

---

### Post by apoth on 2010-10-31
> **apoth said:**
> 
```
sudo dd if=/dev/disk1**s1** of=/dev/disk0s3 bs=1m
```


Needed to add the partition! Finally works now... at least I get to choose to try Ubuntu and pick the language - display goes blank then but at least there are things I can try now!

Many thanks!

---

### Post by apoth on 2010-10-31
Next problem!

I've got to a desktop with the installer. Got networking and graphics working as they should.

When I come to try and actually run the install it seems to hang just after I enter my user details, at the bit where it cycles through the marketing images.

It says Detecting file systems... and the last line of text in the expandable console is:

```
Oct 31 22:59:25 ubuntu ubiquity[16791]: Step_before = stepUserInfo
```

I've tried putting a / mount point on /dev/sda4 - either with it formatted as ext3 or ext4, same results. I've also told it to put grub on that partition too - is that reasonable?

Any ideas? Thanks again.

---

### Post by sanicki on 2010-12-02
> **apoth said:**
> 
When I come to try and actually run the install it seems to hang just after I enter my user details, at the bit where it cycles through the marketing images.

It says Detecting file systems... and the last line of text in the expandable console is:

```
Oct 31 22:59:25 ubuntu ubiquity[16791]: Step_before = stepUserInfo
```


Was there a solution? I'm stuck in the same spot.

---

### Post by notebookshopper on 2010-12-03
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]I have two other partitions than OSX - one large ready for Ubuntu, one smaller one with the iso dd'd onto it.

Refit gives me the OSX icon and a legacy hard disk diamond icon - which leads to just the text 'missing operating system' being shown.[/FONT][/FONT][/COLOR]

---

### Post by zeigerpuppy on 2011-02-07
I haven't been able to get the 10.10 install image booted on my macbook air 11" and rEIt
I have tried USB booting and making a partition.  I tried USB pendrives made in Windows and OS X (with the usual methods).
I also tried dd of just the partition and the whole disk and installing to a variety of partition types.
The image fails to boot with:
Missing operating system
No bootable device found

Here is the partition report, the install image is copied to partition 3.

Any suggestions?

*** Report for internal hard disk ***

Current GPT partition table:
#      Start LBA      End LBA  Type
1             40       409639  EFI System (FAT)
2         409640    117597143  Mac OS X HFS+
3      117860352    137390079  Basic Data

Current MBR partition table:
# A    Start LBA      End LBA  Type
1              1       409639  ee  EFI Protective
2         409640    117597143  af  Mac OS X HFS+
3 *    117860352    137390079  0b  FAT32 (CHS)

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

Partition at LBA 117860352:
Boot Code: Unknown, but bootable
File System: Unknown
Listed in GPT as partition 3, type Basic Data
Listed in MBR as partition 3, type 0b  FAT32 (CHS), active

---

### Post by zeigerpuppy on 2011-02-09
As a follow on, I managed to get the macbook to triple boot.
I gave in to the apple tax and bought a (second-hand) superdrive.  I'm sure it is possible with USB booting but there's no easy way I could find to get ubuntu to boot.  (Windows was OK via this method - [http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/) )

So with the superdrive, use the 'alt' boot method to bring up the CD
Then the ubuntu live cd boots fine (with the nomodeset option).

As the MBR can only have 4 partitions visible, it's important to have this order:

1) EFI  -fat32
2) OS X -HFS+
3) Windows -ntfs
4) Ubuntu /boot -ext3
5) Ubuntu / - ext3
6) swap

I installed grub2 to the boot partition using the installer.

You can also use partition 4 as shared storage (formated ext3) and it can be r/w mounted in Windows7 and OS X (see macfuse and fuse-ext2).

I still have some weirdness with grub loading before windows (i think i may have installed grub to the MBR by accident on one of my trials), but that's a minor annoyance and it works well overall.

---

### Post by srs5694 on 2011-02-09
> **zeigerpuppy said:**
> As the MBR can only have 4 partitions visible, it's important to have this order:

1) EFI  -fat32
2) OS X -HFS+
3) Windows -ntfs
4) Ubuntu /boot -ext3
5) Ubuntu / - ext3
6) swap

Actually, the order of partitions in the GPT and the order of partitions in the MBR do not need to be correlated. The most common form of the gptysync utility just blindly converts the first three partitions it finds (possibly excluding some, but I'm not positive of that); however, I've heard of a version of gptsync that's more flexible, and my own [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) is much more flexible.

My own recommendation, for best safety and flexibility, is to put any parttion(s) you want to hybridize at the end of the disk. That way, the protective partition in the MBR will cover all the other partitions, thus doing its job of protecting them from damage by errant GPT-unaware utilities. In the case of a triple-boot system, only Windows and any shared-data partition that should be accessible to Windows need to be in the MBR; both Linux and OS X are perfectly happy on GPT-only partitions. Thus, I'd put Windows at the end of the disk and use GPT fdisk to create the hybrid MBR.

---

### Post by zeigerpuppy on 2011-02-09
A Good point regarding protecting partitions.

I chose the scheme above to allow a shared data partition (ext3) which all os's can see, but it does make me a little uneasy that this partition also has my ubuntu boot information on it!
I guess there's also some utility in having the rEFIt MBR/GPT sync available from the boot menu.

---

### Post by bilallucky on 2011-02-11
You should install Refit on your [Macbook air]("http://www.letmedefine.com/apple-macbook-air/") it gives you the OSX icon and a legacy hard disk diamond icon.

---

### Post by lucifer613 on 2011-02-13
> **bilallucky said:**
> You should install Refit on your [Macbook air]("http://www.letmedefine.com/apple-macbook-air/") it gives you the OSX icon and a legacy hard disk diamond icon.
Thank you! :D:D:D

---

