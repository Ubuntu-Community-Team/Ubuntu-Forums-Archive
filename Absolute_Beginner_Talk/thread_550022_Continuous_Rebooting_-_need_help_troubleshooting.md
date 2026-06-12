---
title: "Continuous Rebooting - need help troubleshooting"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by scram69 on 2007-09-13
Yesterday, after a crash, my Ubuntu Feisty machine went into a continuous reboot cycle.  It will get to the Ubuntu splash screen (past the Grub stage) and once the little orange bar gets about 1/5th of the way across, the machine reboots.

I tried the "safe boot" option, and the last message I see before the reboot is "loading boot files".

I can boot up on the install disk, but I don't know what to look for.  The last dmesg file was from before the initial crash, and contains a series of "md: array md0 already has disks!"  So, to be safe, while booted on the install disk, I commented out the /dev/md0 from my /etc/fstab.  However, that did not fix the continuous reboot cycle.  The problem is, no more dmesg files are being generated, so I'm not sure where to look for error messages relevant to the problem

Any suggestions?

---

### Post by Happy_Man on 2007-09-13
Try checking whether your HDD somehow got corrupted, perhaps preventing Ubuntu from booting up.

---

### Post by philinux on 2007-09-13
Sounds like you need to run fsck on your system from the live cd.

---

### Post by scram69 on 2007-09-13
> Sounds like you need to run fsck on your system from the live cd.

Sorry, should have mentioned in my initial post that while booted on the CD I did run
e2fsck -y -f -v /dev/hda1 
on the main ubuntu partition (ensuring it wasn't mounted).  It ran through and reported 0 bad blocks.  But the continuous rebooting problem persisted...

---

### Post by scram69 on 2007-09-13
A follow up question - 

fsck only runs on the main (ext3 filesystem) partition.

Is there another flavor of file system check that can be run on the boot partition?

---

### Post by philinux on 2007-09-13
As I remember from the live cd 
sudo fsck /dev/hda1 or whatever hard drive it is should check the whole harddrive.

---

### Post by psusi on 2007-09-13
What type of filesystem is your boot partition?

---

### Post by scram69 on 2007-09-13
> What type of filesystem is your boot partition?

Good question.  Its whatever the Ubuntu installer decided to make it.  All I know is that when I try e2fsck or fsck on /dev/hda2 (the boot partition), I get an error message about not being able to read it.  

Could that be the problem - my boot partition was somehow completely blown away?  If so, how would Ubuntu even begin to boot?

---

### Post by philinux on 2007-09-13
Post result of
sudo fdisk -l

---

### Post by Happy_Man on 2007-09-13
GRUB handles the beginning (up to and until the kernel takes over). Possibly, once GRUB hands it off to the kernel boot processes on the boot partition, it screws up.

---

### Post by scram69 on 2007-09-13
> GRUB handles the beginning (up to and until the kernel takes over). Possibly, once GRUB hands it off to the kernel boot processes on the boot partition, it screws up.

Ok, that makes sense.

> Post result of
sudo fdisk -l

I know I looked at that last night, but in all my flailing about, I can't honestly remember what it said.  I'll look again as soon as I get home tonight.
Thanks-

---

### Post by scram69 on 2007-09-13
> **philinux said:**
> Post result of
sudo fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4787    38451546   83  Linux
/dev/hda2            4788        4998     1694857+   5  Extended
/dev/hda5            4788        4998     1694826   82  Linux swap / Solaris
```

Turns out my understanding of hda1 vs hda2 was backwards - hda1 is the boot partition.  

```
ubuntu@ubuntu:~$ sudo fsck -y -v /dev/hda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hda1: clean, 145442/4807488 files, 1362940/9612886 blocks
ubuntu@ubuntu:~$ sudo fsck -y -v /dev/hda2
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda2
Could this be a zero-length partition?

```

Note: I did _not_ mount hda before I ran fsck.  However, I can mount it when booted on the CD, and browse the filesystem - everything appears to be intact!  I can even use the Disk Usage Analyzer to scan the file sizes... What would make fsck complain?

---

### Post by scram69 on 2007-09-14
Nevermind that last comment - after further research, I now realize that hda2 is simply the container for the swap space (hda5).

So I'm back where I started - a seemingly ok hard disk that won't boot properly, and no real leads on how to diagnose the problem...

---

### Post by philinux on 2007-09-14
```
sudo fsck -y -v /dev/hda1
``` 

From the live cd. I'd run it without the -y. I think without the /dev bit it should just run through the fstab file.

---

### Post by scram69 on 2007-09-14
> **philinux said:**
> ```
sudo fsck -y -v /dev/hda1
``` 

From the live cd. I'd run it without the -y. I think without the /dev bit it should just run through the fstab file.

Yes, that's correct.  It does - and keeps telling me that /dev/hda1 is "clean", with or without the "-y".

At this point, I'm under the assumption that since I can boot and run the system perfectly well using the Live CD, that this isn't a hardware problem (except for /dev/hda1).  But fsck says there's nothing wrong with the file system ... 

Could there be a problem with one of the files in /boot or /boot/grub?  How would I go about troubleshooting that?

---

### Post by philinux on 2007-09-14
Post the contents of /boot/grub/menu.lst

---

### Post by psusi on 2007-09-14
It sounds like your kernel is corrupted or something like that.  From the livecd you can mount the hard drive and install the debsums package, then run debsums -c to check all of the files of installed packages to see if any of them have been modified.

---

### Post by bubbalouie on 2007-09-14
Perhaps you can remove the kernel image and restore one of the **.bak** files in **/boot/**, make certain the **menu.lst** reflects this change.

I had a boot issue a while back, restoring an older kernel addressed the problem, I followed it up with an adept update and all was good.

Good Luck.

---

### Post by scram69 on 2007-09-14
> **bubbalouie said:**
> Perhaps you can remove the kernel image and restore one of the **.bak** files in **/boot/**, make certain the **menu.lst** reflects this change.

I had a boot issue a while back, restoring an older kernel addressed the problem, I followed it up with an adept update and all was good.

Good Luck.

Are these the files in /boot/ that begin with init* and contain the kernel version in the name?  I actually gave that a try last night: I noticed I had a .bak version that was older than the current non-.bak file, so I re-named the two -  but this didn't help.  However, I did not edit menu.lst.  I didn't think I needed to as I re-named the older version the same as the newer version, after moving the newer version.  What do I need to change in menu.lst?

---

### Post by bubbalouie on 2007-09-14
It sounds like you did the right thing, grub needs to point to the right files. In my case an update had gone awry and caused the problem, what you just did fixed my problem.

If grub can't find something, it tells you in no uncertain terms that it can't find the file.

I am inclined to agree with **psusi** that the issue is most probably a broken kernel.

Perhaps the following may have a few clues:

**/var/log/kern.log**

If you post the contents maybe the forum can help, I can look and maybe help, but I must warn you, I am not an expert yet (I get by on "educated" guess work rather than experience sorry).

As an aside, You could tar you home directory, reinstall Ubuntu, then restore the home directory (you will of course need to reinstall all of your apps), this should fix things more or less, though it is rather drastic, however, if you do go this route, it's possible to EASILY backup you whole root partition in case something like this ever happens again. I do this myself ever since that last nasty update I had (honestly I was lucky to figure out an easy fix).

Once again, good luck, and if you have Q's just ask or PM me (warning: not an expert, but I am happy to help).

Ryan

---

### Post by psusi on 2007-09-14
You might just try reinstalling the kernel.  Mount the drive from the livecd, chroot into it, and apt-get install --reinstall linux-whatever-version.

---

### Post by scram69 on 2007-09-15
> **bubbalouie said:**
> It sounds like you did the right thing, grub needs to point to the right files. In my case an update had gone awry and caused the problem, what you just did fixed my problem.

If grub can't find something, it tells you in no uncertain terms that it can't find the file.

I am inclined to agree with **psusi** that the issue is most probably a broken kernel.

Thanks for your help - I think that may be the issue as well.  Last night I realized that my Feisty installation actually gives me a choice from the grub menu of loading one of two kernel verisons: -15 and -16 (the default).

So I chose the -15 version (in safe mode) and the boot process made it considerably farther than using the default -16.  It stopped and rebooted after I saw a message about my raid array, something to the effect of "md0: unclean array".  This was after I had commented out the /dev/md0 line in /etc/fstab; I guess there's more I need to do in order to prevent the system from trying to mount the array on boot.  I probably need to rename the mdadm.conf file...

Unfortunately, even with the -15 version, things didn't progress far enough for a log file to get written (dmesg, messages, syslog, and kern.log all have time stamps from before the original crash) - makes it difficult to debug.

So I would like to take psusi's suggestion and reinstall the kernel.  

When you say "chroot into it", do you mean (with the Live CD, my filesystem gets mounted as /media/disk/)
```
sudo chroot /media/disk/ 
```? In order to make that the root of the filesystem for the apt-get install command?

---

### Post by psusi on 2007-09-15
Yes, after that chroot command, that terminal acts like /media/disk is / so any commands you do from there are done as if you had booted normally from the hard disk.

---

### Post by scram69 on 2007-09-17
well I tried
```
sudo apt-get install --reinstall linux-image-2.6.20-16-generic
```
everything seemed to go well, so I rebooted.

The first time, I got into the blue screen with an X server error:
"NVIDIA(0): Failed to load the NVIDIA Kernel Module

Then, after exiting that, I was back into the continuous reboot cycle.

However, provided I comment out the /dev/md0 line in my /etc/fstab, I can enter the grub menu and boot up into the 2.6.20-15 kernel just fine.  Apparently, /dev/md0 has disappeared, and attempts to mount it with fstab wreak havoc.

When I look at /var/log/messages, I see:
```
Sep 16 21:27:42 mediaserver kernel: [   34.647825] EXT3-fs: mounted filesystem with ordered data mode.
Sep 16 21:27:42 mediaserver kernel: [   34.678639] md: md0 stopped.
Sep 16 21:27:42 mediaserver kernel: [   34.697939] mdadm[2693]: segfault at 0000000000000004 rip 000000000041567c rsp 00007fff97aaec20 error 4
Sep 16 21:27:42 mediaserver kernel: [   34.706476] md: md0 stopped.
Sep 16 21:27:42 mediaserver kernel: [   34.733561] md: hda has invalid sb, not importing!
Sep 16 21:27:42 mediaserver kernel: [   34.733565] md: md_import_device returned -22
```

1) did I use the wrong argument (linux-image-2.6.20-16-generic) when I tried to reinstall the kernel?

2) I'm not sure what to make of the md messages: hda is not part of my raid array (it was sda thru sdd); I don't know what to do with the mdadm segfault, but I'm assuming I'll have to fix it in order to get my /dev/md0 back?

---

### Post by psusi on 2007-09-17
Wow... what does /etc/mdadm.conf look like?

---

### Post by scram69 on 2007-09-17
> **psusi said:**
> Wow... what does /etc/mdadm.conf look like?I don't have it in front of me, but to create mdadm.conf, I did:
```
mdadm --detail --scan >>/etc/mdadm.conf
```This created a one line file that begins with "ARRAY /dev/md0 ..."

**Note:**  in order to get the 2.6.20-15 kernel to boot and create the /var/log/messages file that I posted above, I had to rename /etc/mdadm.conf.

---

### Post by scram69 on 2007-09-17
Also, I realize that I might have had problems with the nvidia driver (I used Envy to install originally) when I did the kernel reinstall.
Is there a way to reinstall the kernel and the nvidia kernel module at the same time, so that things work upon reboot?  Or, should I try and modify xorg.conf to some generic settings, reboot, and then use Envy to reinstall the nvidia driver?

---

### Post by scram69 on 2007-09-18
After reinstating the original mdadm.conf file, I tried to manually assemble the raid array:
```
sudo mdadm --assemble --scan
```
this is followed by something like "md0 assembled with 4 devices", and then about 10 seconds later, a reboot.

I even tried booting on the liveCD, installing mdadm using synaptic, and manually assembling - same thing: the machine reboots about 10 seconds after assembling the array.  That pretty much rules out some corrupt file on my system drive from causing the problem.

---

### Post by alienexplorers on 2007-09-18
First use ENVY to remove your drivers, then have ENVY reinstall the drivers.  i had a similar problem that happen after a kernel update and it made my machine go nuts.  Reloading my graphic drivers fixed the problem.

---

### Post by psusi on 2007-09-18
Wow, sounds like a hardware problem then.  You have a 4 drive array?  Your power supply may not be up to that load and browns out when all the disks are accessed at once.

---

### Post by scram69 on 2007-09-21
> **psusi said:**
> Wow, sounds like a hardware problem then.  You have a 4 drive array?  Your power supply may not be up to that load and browns out when all the disks are accessed at once.

So I ordered a new 550W ATX v.2 power supply, the kind that guarantees 18A on the 12V bus.  It arrived last night.  Unfortunately, that wasn't the problem.  :(  Even removing all drives, cards, fans, etc. except for the system HD, graphics card, and SATA drives, I get the same behavior - the system reboots when I attempt to assemble the array.

What is really, really maddening is that on boot, the system will assemble any combination of 3 of the 4 drives (by physically disconnecting the power connector to any one drive), and then complain about degradation due to the missing disk.  It doesn't matter which drive I disconnect; I've tried all 4.
But when I try to assemble the full array, either manually or on boot, the system reboots.  It reboots on assembly - I don't even get a chance to try and mount the thing. 

When I do unplug one drive (any single drive, doesn't matter which one), here's what I see:```

steve@mediaserver:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon May  7 21:31:55 2007
     Raid Level : raid5
    Device Size : 488383872 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Sep 12 15:58:54 2007
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : bc7a4d90:bd286a91:c109596b:d7e29b7e (local to host mediaserver)
         Events : 0.161

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       8       33        3      active sync   /dev/sdc1
```

Unfortunately,
```
steve@mediaserver:~$ sudo mount -t xfs /dev/md0 /var/lib/mythtv
mount: /dev/md0: can't read superblock
```

---

### Post by psusi on 2007-09-21
It still sounds like a power issue.  Try this:

sudo dd if=/dev/sda of=/dev/null &

Repeat for each disk.  This should stress them fairly well.

---

### Post by scram69 on 2007-09-23
psusi - thanks,  I finally had some time to sit down and systematically troubleshoot the individual drives by unplugging them one at a time and restarting.

using the dd command, going through /dev/sda[a,b,c]1 one at a time, I was able to determine the bad drive as it caused a reboot during the read.

I pulled it out, replaced it, and was able to rebuild the array after manually stopping, force-starting, and adding the new drive (mdadm -S, mdadm -Af, mdadm -a)

Thanks for your help and patience-

---

