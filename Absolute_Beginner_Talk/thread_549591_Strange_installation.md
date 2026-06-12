---
title: "Strange installation"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-09-12
Ok.  Was having trouble installing with the live cd.  So I downloaded the text one, and ran it.  The first time it installed successfully, but I was an idiot and must have misspelled my username because it wouldn't let me log in.

So I reinstalled it.  This time the installation locked up.

3rd try.  It installed fine, I can log in - no internet.  I knew that would happen because it told me it didn't locate any networking component when it was installing - but thats not what I am worried about right now.

I booted up XP, so I could tackle the networking issue, but checked the disk manager in mmc first, to make sure it partitioned right.

It looks like this:
[IMG]http://i46.photobucket.com/albums/f120/waste301/WTF.jpg?t=1189640958[/IMG]

I am about to apply my forehead to my desk in a forceful manner.

All I want is 2 partitions, 30% windows XP, 70% ubuntu.

Please help.

---

### Post by waste301 on 2007-09-12
^bump.  Please help.

---

### Post by diatribe on 2007-09-12
if you install ubuntu with a seperate home partition, that will use three partitions itself.  is this what you did?

---

### Post by skyjacker on 2007-09-12
Most hard drives will allow only four (4) partitions on them.

---

### Post by waste301 on 2007-09-12
> **diatribe said:**
> if you install ubuntu with a seperate home partition, that will use three partitions itself.  is this what you did?

I specified (h0,0) for GRUB.  I said 70% when it asked about partition size.  I'm not exactly sure what you mean by specify.

> **skyjacker said:**
> Most hard drives will allow only four (4) partitions on them.

I have no idea how it happened, but can I get rid of it?  How many OS's are on my system right now?

---

### Post by diatribe on 2007-09-12
2 it would seem.  from a terminal in ubuntu type 

sudo fdisk -l

and post the output

---

### Post by waste301 on 2007-09-12
> **diatribe said:**
> 2 it would seem.  from a terminal in ubuntu type 

sudo fdisk -l

and post the output

OK - back in a minute.

---

### Post by Bothered on 2007-09-12
It's a bit tricky to diagnose it from the Windows partition utility, as it doesn't recognise any non-Windows partitions. Executing:

```
sudo fdisk -l
```

when in ubuntu will give the output needed.

EDIT: Too slow :-)

---

### Post by waste301 on 2007-09-12
Here it is.

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        2837    22731975    7  HPFS/NTFS
/dev/sda3            2838        7257    35503650   83  Linux
/dev/sda4            7258        9726    19832242+   5  Extended
/dev/sda5            9440        9726     2305296   82  Linux swap / Solaris
/dev/sda6   *        7258        9342    16747699+  83  Linux
/dev/sda7            9343        9439      779121   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 263 MB, 263454720 bytes
9 heads, 56 sectors/track, 1020 cylinders
Units = cylinders of 504 * 512 = 258048 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     3709864     4044566    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(3709863, 7, 22)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(4044565, 2, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?     3376031     7086113   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(3376030, 6, 26)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(7086112, 8, 50)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?           6           6           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(5, 0, 54)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(5, 0, 53)
Partition 3 does not end on cylinder boundary.
/dev/sdb4               1     6815702  1717556736    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(6815701, 2, 56)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
matt@mattspc:~$ 

So what am I looking at guys?  I'd like to have my hard drive in to major partitions.  30% windows 70% ubuntu. Is possible?

---

### Post by diatribe on 2007-09-12
hm, you have two hard drives?  also, you have two swap partitions, did you try to install ubuntu twice?  and please type 

sudo mount

amd post the output

---

### Post by waste301 on 2007-09-12
> **diatribe said:**
> hm, you have two hard drives?  also, you have two swap partitions, did you try to install ubuntu twice?  and please type 

sudo mount

amd post the output


Please refer to my first post.  I explained what happened there.  I'll go get sudo mount.

---

### Post by Bothered on 2007-09-12
Thats a bit odd - it looks a bit like you have ubuntu installed twice (that's what the two swap partitions suggest). You could try reinstalling ubuntu, this time using gparted to create the space for ubuntu prior to running the installer (deleting the existing linux partitions, including the extended partition). gparted can be accessed from the ubuntu LiveCD at System->Administration->GNOME Partition Editor. I recommend caution before trying this - backup all essential data.

Incidentally, your first partition (the FAT partition) could contain recovery files or other utilities that came with your PC.

EDIT: I see, the FAT partition contains Dell utilities, I missed that.

---

### Post by angryfirelord on 2007-09-12
Ok, try this. Put the Ubuntu cd in and launch the installer. When the partition options come up, click Manual.

Now, this may screw up Windows in its entirely, but delete all partitions except for any that say FAT or NTFS. Then, create one / partition and one swap partition for Ubuntu.

---

### Post by waste301 on 2007-09-12
sudo mount 

/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
matt@mattspc:~$ 

If I want to just scrap it and reinstall, what partitions should I delete, and how do you create a partion for ubuntu to recognize and install itself into?

---

### Post by diatribe on 2007-09-12
use manual configuration in the partiton setup screen, you can safely remove

dev/sda3 2838 7257 35503650 83 Linux
/dev/sda4 7258 9726 19832242+ 5 Extended
/dev/sda5 9440 9726 2305296 82 Linux swap / Solaris
/dev/sda6 * 7258 9342 16747699+ 83 Linux
/dev/sda7 9343 9439 779121 82 Linux swap / Solaris

those partitions.

When you set up your partitons you will need a partiton for / a partition for swap (equal to your ram, or twice your ram if you have below a GB) and optionally a /home partition.  you will need to keep your utilities and windows partitions (sda1 and sda2)

---

### Post by waste301 on 2007-09-12
> **angryfirelord said:**
> Ok, try this. Put the Ubuntu cd in and launch the installer. When the partition options come up, click Manual.

Now, this may screw up Windows in its entirely, but delete all partitions except for any that say FAT or NTFS. Then, create one / partition and one swap partition for Ubuntu.

I can't do that.  If I destroy windows I'll lose internet access.  I'd have to remove everything again and reinstall windows, my ISP software etc.

---

### Post by waste301 on 2007-09-12
> **diatribe said:**
> use manual configuration in the partiton setup screen, you can safely remove

dev/sda3 2838 7257 35503650 83 Linux
/dev/sda4 7258 9726 19832242+ 5 Extended
/dev/sda5 9440 9726 2305296 82 Linux swap / Solaris
/dev/sda6 * 7258 9342 16747699+ 83 Linux
/dev/sda7 9343 9439 779121 82 Linux swap / Solaris

those partitions.

I assume you are saying remove those partitions, and then reinstall from scratch?

---

### Post by diatribe on 2007-09-12
it would be the best option yes

---

### Post by Bothered on 2007-09-12
> **waste301 said:**
> I can't do that.  If I destroy windows I'll lose internet access.  I'd have to remove everything again and reinstall windows, my ISP software etc.

Editing partitions can always result in damage to other partitions on the drive. It is up to you whether to take the risk or not.

I would personally launch the ubuntu LiveCD, delete partitions 3, 4, 5, 6 and 7 (one of which is an extended partition) using gparted, then launch the alternate CD install and run the installer, selecting "Use free space" at the partitions menu.

Note that once the partitions have been deleted you will be unable to boot Windows until ubuntu is reinstalled using the alternate CD, as the boot loader will have been deleted.

---

### Post by Bothered on 2007-09-12
EDIT: Duplicate post

---

### Post by waste301 on 2007-09-12
> **diatribe said:**
> it would be the best option yes

OK - I'll try it.  I noticed that you said remove 5 partitions.  There are only 6 on my drive I can see in windows.  You're sure all five, I can't lose windows or I screwed.

---

### Post by diatribe on 2007-09-12
windows and linux report theior partitons differently, as long as you remove partitons that identify as either ext3 or linux swap, DO NOT TOUCH ANYTHING THAT SAYS NTFS OR FAT, you will be ok

---

### Post by Bothered on 2007-09-12
> **waste301 said:**
> You're sure all five, I can't lose windows or I screwed.

One of the five partitions mentioned above is an extended partition - i.e. a partition containing other partitions (the green box displayed in windows).

---

### Post by diatribe on 2007-09-12
> **Bothered said:**
> Editing partitions can always result in damage to other partitions on the drive. It is up to you whether to take the risk or not.

I would personally launch the ubuntu LiveCD, delete partitions 3, 4, 5, 6 and 7 (one of which is an extended partition) using gparted, then launch the alternate CD install and run the installer, selecting "Use free space" at the partitions menu.

Note that once the partitions have been deleted you will be unable to boot Windows until ubuntu is reinstalled using the alternate CD, as the boot loader will have been deleted.

this is also a good idea

---

### Post by waste301 on 2007-09-12
> **Bothered said:**
> Editing partitions can always result in damage to other partitions on the drive. It is up to you whether to take the risk or not.

I would personally launch the ubuntu LiveCD, delete the partitions 3, 4, 5, 6 and 7 (one of which is an extended partition) using gparted, then launch the alternate CD install and run the installer, selecting "Use free space" at the partitions menu.

Note that once the partitions have been deleted you will be unable to boot Windows until ubuntu is reinstalled using the alternate CD, as the boot loader will have been deleted.

Thanks, I have another issue as well.  This is a new dell machine.

1 223-1769 Vostro 400, Intel Core2 Duo CPU E6550 (2.33GHz, 1333FSB 4MB L2)
1 311-7366 2GB DDR2 SDRAM 800MHz, Dual Channel DT
1 310-9322 Dell USB Keyboard
1 320-5667 Dell 22 inch Wide E228WFP Analog Flat Panel Monitor
1 320-5760 256MB NVIDIA GeForce 8600GT 2DVI
1 341-4988 80GB Serial ATA Hard Drive 7200RPM, 8MB Cache
1 341-4742 No Floppy Drive Requested
1 420-7369 Genuine Windows XP Home
1 420-7243 CyberLink PowerDVD 7.0 DVD Playback
1 310-9440 Windows XP Home backup CD
1 420-7180 Dell Support 3.4
1 420-7286 GOOGLE SEARCH PORTAL ON
1 313-5798 Dell Resource CD, Vostro 400
1 310-9326 Dell Scroll Mouse
1 430-2501 Integrated 10/100 Ethernet
1 313-5469 No Modem Requested
1 420-7275 Adobe Acrobat Reader
1 313-5456 16X DVD+/-RW Drive
1 420-7241 Roxio Creator
1 313-5672 Integrated 7.1 Channel Audio
1 313-5461 No speakers
1 420-7189 DellNetwork Assistant 1.7
1 420-7262 No Pre-installed Security Software
1 420-7280 No Internet Service Provider Requested
1 420-7281 No Pre-installed Productivity Software
1 412-0359 Soft Contracts - Qualxserve
1 983-4250 Warranty Support,Initial Year
1 987-6849 No Warranty, Year 2 and 3
1 983-8540 Type 3 Contract - Next Business Day Parts and Labor On-Site Response, Initial Year
1 988-0387 Dell Hardware Warranty PlusOnsite Service, Initial Year
1 987-7479 VOSTRO,Datasafe 10GB,1YR(Incl w/price)
1 420-7368 Dell DataSafe 2.0 Online, 10GBfor 1 Year Free (for ABU only)
1 960-8851 1YR AUT. PC TUNE UP,VOSTRO, Included in Price
1 420-7367 PC Tune-up, 1 Year (For English OS only)
1 462-4506 Purchase is NOT intended for resell
1 310-8591 You have chosen a Windows XP System
1 310-8977 S and P Drop-in-Box Marcom forBSD Systems Box

The umbuntu installer is not recognising any network devices on installation.  Is there anything I can do about that?

I will check back later to see if you responded, but I am going to be gone a while as I fix the partitions and reinstall.

---

### Post by Bothered on 2007-09-12
One more thing - if you do use gparted in the LiveCD, you may need to periodically enter the commands "sudo umount -a" and "sudo swapoff" in a terminal, as the LiveCD may mount partitions you want to delete. Enter these commands in a terminal is gparted refuses to delete partitions.

---

### Post by diatribe on 2007-09-12
that doesnt specify what model nic you have

---

### Post by waste301 on 2007-09-12
> **diatribe said:**
> that doesnt specify what model nic you have

Oops.  Device manager says:intel 82562V-2 Network connection.

> **Bothered said:**
> One more thing - if you do use gparted in the LiveCD, you may need to periodically enter the commands "sudo umount -a" and "sudo swapoff" in a terminal, as the LiveCD may mount partitions you want to delete. Enter these commands in a terminal is gparted refuses to delete partitions.

I have no idea how to use gparted, so I'm going to use windows live CD install to delete the partitions.  I would be most comfortable deleting them from windows if possible.  Then use the alt CD to reinstall.

I've got to install a printer and print out your instructions.  So I'll do that and check back here before blast-off.

---

### Post by Bothered on 2007-09-12
> **diatribe said:**
> windows and linux report theior partitons differently, as long as you remove partitons that identify as either ext3 or linux swap, DO NOT TOUCH ANYTHING THAT SAYS NTFS OR FAT, you will be ok

Agreed. Do not alter the first two partitions on the drive.

---

### Post by Bothered on 2007-09-12
> **waste301 said:**
>  I'm going to use windows live CD install

That should work, although I've never used it. However, looking at your first post I would take care to select the correct partitions for deletion (they're not listed in order in your screen capture).

---

### Post by waste301 on 2007-09-12
> **Bothered said:**
> Agreed. Do not alter the first two partitions on the drive.

Good, that makes me feel much more confident.  I was wondering why you wanted me to delete 5 partitions in ubuntu, when I only saw 4 in windows.  But I was gonna take you guys on faith : P

If you have any insight on the networking issue, I'd be extremely grateful.  Trying to get ubuntu online is what got me in this mess in the first place, I'm just trying to get back where I started.  Until I can get it online I have to stick with windows.

---

### Post by diatribe on 2007-09-12
> **Bothered said:**
> That should work, although I've never used it. However, looking at your first post I would take care to select the correct partitions for deletion (they're not listed in order in your screen capture).

seconded.  I don't know anything about windows parttioning but take care not to edit any windows filesystems, as was stated they are not listed in order in windows apparently

---

### Post by waste301 on 2007-09-12
[IMG]http://guidesmedia.ign.com/guides/16387/starman.jpg[/IMG]

**diatribe**   **Bothered**


You guys each get a gold star.  I appear to have a stable windows XP taking up 30% of my drive, and a stable ubuntu on the other 70%.  The only thing I need to do now is get ubuntu online, but I think that is a project for another day.

I award 1 internet apiece, and my gratitude.

---

### Post by Bothered on 2007-09-13
Glad to hear it :-)

---

