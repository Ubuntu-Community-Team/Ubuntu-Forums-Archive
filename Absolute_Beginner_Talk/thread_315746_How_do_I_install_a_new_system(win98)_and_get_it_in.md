---
title: "How do I install a new system(win98) and get it in Grub?"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by garry4o on 2006-12-09
I have an HP laptop, purchased about a year ago. It came with WinXP installed. Using PartitionMagic, I installed several data partitions, all but 1 (the WinXP primary) in logical partitions. :) 

Recently, driven by continuous bugging by WGA (which passes my machine as it should), numerous reports about Vista WGA's super annoyances, and suspicions about new XP WGA versions,:evil:  I used PartitionMagic to create a new primary partition (That makes 2), and formatted it ext3, and another logical partition formatted Linux Swap. 

I successfully installed Ubuntu 6.06 in those two. I am happy and on my way to complete conversion to Ubuntu. (I tried several earlier Linux Distros, but was unable to get any to boot successfully on my then desktop.) I switch back and forth (Win to Ubuntu) with no problems. Some of the apps are not completely compatible, so I need both for a while.

I wish to add another OS (not Linux), which will take another primary partition.  Can I create and setup the new partition for new OS under Linux, or shall I fall back to PartitionMagic. Prior to this laptop, I ran large desktops with multiple versions of Windows installed. I used System Commander as the multiple boot loader. I know those two will work (I've used them for about 10 years at different levels and never have had a problem). I have not installed System Commander on this laptop, and in fact can no longer find my original floppies for a new install. 

Can I use gparted to hide the WinXP and Linux partitions so that only the new partition will show when I do the actual install?

How will I get Grub to find the new OS once I install it? The menu.lst has not changed since my first major update to 6.06 - 187 updates.

What has triggered much of this is I now (maybe too late) feel I need a boot floppy to possibly restore my MBR, in the event some of these experiments go awry. The final touch is that I went to Microsoft website to find out how to get a WinXP boot floppy. The only way is to download a multi floppy suite to start WinXP far enough to let a restore CD finish a WinXP install. In order to do that, I must download the latest version of WGA (which I think I already have) and prove my laptop XP is "OK":twisted: . I decided that was the last straw for me. I'm sure that as soon as I can, I'm going to move all my personal stuff to Ubuntu apps and keep XP to run my Lexmark all-in-one printer for copies scans and color. BTW, the floppy is a USB one that works fine, even allowing booting.

---

### Post by louieb on 2006-12-10
Why would the Writers Guild of America be bugging you?

---

### Post by randiroo76073 on 2006-12-10
Quick question, do you still have a desktop you could use to backup to, or external hdd?  I would get a copy of partimage, image Ubuntu & possibly XP[depends on need], or at least backup anything I didn't want to loose before starting.
98se would be a good windoz for needed apps.  If further info on 98se updates needed PM me for info, MS no longer supports.
It can be done, patience & double check steps will make it easier.
This is best info for you:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Other sites for info:
[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by garry4o on 2006-12-10
Thanks for the help. I've quickly looked at all the resources you mentioned, and I wish I had known of them prior to my first install - I would have done some things differently.

In answer to your first question-no, I no longer have the desktop. I retired, and bought a winter place in Florida (I live in New York) where I spend Jan-Apr. I bought the laptop to allow easy transport and chose HP based on reputation. I can tell you that WinXP is large, but when you add on HP's additions, you have a boot monster. After I purchased the XP compatible PartitionMagic, I resized the boot partiton, created some logical partitions, and began to move legacy data from cd to them. I also converted the XP boot partition to Fat32 from NTFS.

I like your idea about Win98se. I have an install cd for it already, though I haven't used it since it first came out. There may be another issue that I don't know the answer to. Win98se cd requires a boot floppy for the install. Now I have added a usb floppy drive and booted a DOS 6.22 disk that was marked a Win98 installer disk. It boots fine, except that it can't see the hard disk. I don't know if this is because the grub mbr is in the mbr or perhaps booting from the usb device occurs before the bios is read telling dos about C:. In either case, I can't install until I overcome that problem. Any suggestions here? Perhaps there is a DOS program to force reading the disk?

---

### Post by adrian15 on 2006-12-11
> **garry4o said:**
> 
What has triggered much of this is I now (maybe too late) feel I need a boot floppy to possibly restore my MBR, in the event some of these experiments go awry. The final touch is that I went to Microsoft website to find out how to get a WinXP boot floppy. The only way is to download a multi floppy suite to start WinXP far enough to let a restore CD finish a WinXP install. In order to do that, I must download the latest version of WGA (which I think I already have) and prove my laptop XP is "OK":twisted: . I decided that was the last straw for me. I'm sure that as soon as I can, I'm going to move all my personal stuff to Ubuntu apps and keep XP to run my Lexmark all-in-one printer for copies scans and color. BTW, the floppy is a USB one that works fine, even allowing booting.

With [Supergrub]("http://supergrub.forjamari.linex.org") you can restore both Linux and Windows boot records. It may be what you need.

adrian15

---

