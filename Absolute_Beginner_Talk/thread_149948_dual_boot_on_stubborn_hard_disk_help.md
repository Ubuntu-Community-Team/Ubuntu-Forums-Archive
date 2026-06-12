---
title: "dual boot on stubborn hard disk help?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by buckykat on 2006-03-25
i have been installing ubuntu for the past several days. i started out with v5.10 live cd, and liked it a lot. when i tried to actually install ubuntu, windows wouldn't let me take 10 GB (of its' 60 GB) to put it on. i made a norton ghost backup of windows to an external drive, and tried to install ubuntu again; this time by erasing all partitions on my 60 GB drive, and creating a new 10 GB fat32 partition (i found some instructions on a private site that told me to use fat32.) and a 50 GB ntfs partition. about 22% through the installation, the screen went red, then i got an error message stating that a '1' was found where there should have been a '0'. then it shut down. after a couple hours getting errors like that i just gave up on windows temporarily, and let ubuntu configure the hard drive its' way. now ubuntu works fine but i've already run into some xp exclusivity; i want my windows back but i'm already hooked on ubuntu. that all boils down to:
-need help partitioning drive
-don't need help restoring windows to free space
-would like to know what fat32, ntfs, etc. mean
-no worries about losing ubuntu data
p.s. i already dug a couple linux partitioners (gparted, qtparted) out of the applications menu. they can't make a free space either. i get an 'in use' error even when running those apps from the live cd. i hope that's enough information.

---

### Post by Pragmatist on 2006-03-25
To partition, you need to make sure the drive is unmounted.  If, for example, your hard drive is at /dev/hda, you'd type this (I'm assuming your using the LiveCD so that your running the OS via the CD drive and can unmount your hard drive):
```
umount /dev/hda
```
If it says it isn't permitted, you need to preface with the command **sudo**  so:
```
sudo umount /dev/hda
```

ntfs, fat32, fat16, vfat, ext2, ext3, etc..etc... are filesystem types.  Your hard drive is just a blank media for recording information.  The filesystem is the book keeper.  It organizes the space, has many rules and restrictions, and performs many functions.  For example, a journalling filesystem actually keeps a journal of all the information (in addition to storing it) which helps if there is a power outage or the machine is abruptly shut off, among other benefits.  fat32 (older was fat16), ntfs are all windows/dos filesystems.  ext2, ext3, reiserfs, and many others are linux filesystems. vfat is a kind of 'improved' fat32.  fat32 has certain restrictions on filename lengths, it doesn't retain linux's permissions, time stamps, and other important information.  vfat does allow those things. ntfs is the filesystem for the windows networking OSes like windows NT, windows 2000, and windows XP.  It is an improvement on fat32, is much more secure, and has its own set of restrictions which I don't remember off-hand :)

 Windows is very picky.  It likes to be the first drive, the first partition on that drive and so on.  The best approach is to install windows on a hard drive connected to the first IDE port (this will be called /dev/hda in linux).  Once windows is installed, you install Linux. It will recognize windows and give you a reasonable default partition strategy.  You can make modifications to that default partition strategy during the install process.  So, I would use the LiveCD (I prefer the LiveCD Knoppix, because I'm more familiar with it and because I don't think the Ubuntu LiveCD was designed specifically for this sort of thing) to partition the drive, then install windows, then install Ubuntu.

---

