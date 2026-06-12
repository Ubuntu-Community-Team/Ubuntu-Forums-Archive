---
title: "Overlapped Partition Tables, Bad MBR, won't boot"
date: 2010-08-04
forum: Apple Hardware Users
---

### Post by modelmaker on 2010-08-04
I've been trying to install 10-4 to dual boot with OSX for about a month; have tried on two different Intel Macs, using an external drive and then the internal HD. Have followed different installation scenarios, most recently the clear and lucid instructions here. 
<https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation>

In every case, everything has proceeded normally right up to boot time, when I go to the rEFIt partition tool to sync the partition tables. Then I get the "MBR table is invalid, overlap" condition. And indeed the MBR table ides appear to be hosed.  Ubuntu will not boot.

Here is the rEFIt map:

GPT Table
#            START                         END           TYPE
1                                  1          409639          EFI System (FAT)
2      409640           568714015     Mac OS X HFS+
3      568715264          568717311       Grub2 BIOS Boot
4      568717312          960145407        Basic Data
5      960145408         976773119        Linux Swap

MBR Table
1                                    1                     409639        EE EFI Protective
2 *            409640          568714015        AF Mac OSX HFS+
3                                   1       568717311       EE EFI Protective
4      568717312            568145407        83 Linux 

(I tried to space the above into proper columns - multiple spaces are not retained.)

I'm new to Ubuntu, have no experience with Linux, and aside from the live CD I have no Linux running here. Will appreciate any suggestions &#8230;

Thanks --
<MM>

---

### Post by iShurtugal on 2010-08-04
Did you shrink your mac partition in OS X before installing, or did you do it in the ubuntu installer?
If you did it in the ubuntu installer, try to shrink it from OS X
Did you check your ubuntu cd's Hashes (Md5,SHA1)?  If not, try redownlaod the iso and checking the hashes this time.  I wiped my entire HD once because of a bad fedora iso, and had to use testdisk to get it back.
Also, why a seprate boot partition (I'm guessing thats what it is as it is labeled "Grub2 BIOS Boot")  machines build in the last few years don't need them, and even if you need one, it needs to go at the front of the disk.

---

### Post by modelmaker on 2010-08-05
I wiped a new HD, created an OSX partition to occupy half of it, left the remainder as MT space, installed OSX, installed  rEFIt, then told Ubuntu to install into MT space. 

I did not check hashes on the distribution; don't know how. I will download and burn again.

I used 'advanced' button, installed Grub to /dev/sda3 as instructed by this webpage:
<https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation> (Actually, the options displayed specified sda, no option for '3' or any other number.)

Thanks for your help, iShurtugal.

<mm>

---

### Post by conundrumx on 2010-08-05
Installing GRUB to the MBR (/dev/sda) is a recipe for pain.  The Ubuntu installer won't let you install to /dev/sda# if you're doing the entire setup straight from the installer itself, because none of the partitioning is actually done until you hit "go."

To get around this, I used (G)parted to create the Linux partition layout I wanted, then ran the installer and reformatted the ext4 root partition.  I would also strongly advise you have OSX take the entire disk, then use Boot Camp Assistant to resize.  When you finish, select "Quit" instead of "Reboot and Install."  This is the "correct" way to set your Mac up to boot a legacy (aka, BIOS expecting) OS.

I should just edit that wiki with new information, at the rate I've been posting this...

---

### Post by alphonce on 2010-08-05
I recently installed ubuntu on my imac and heres the way i did it.

first I installed macosx and used disc utility to create 2 partitions, the first with hfs+ for macosx, the other one empty for linux.
then i installed refit.

the i installed ubuntu (lucid 32bit). in the empty space i created first a boot partition (128mb/ext2), then root (/) (15gb) and rest /home (rest), the latter ones ext4.

i installed grub on the boot partition, and everything has worked except one kernel panic, cant mount root vfs.

then i chrooted the linux partitions from the install-cd and just reinstalled grub on the boot partition.

im very new with linux on a mac and just hopes this gives you some help, good luck =)

---

### Post by iShurtugal on 2010-08-06
> **modelmaker said:**
> I wiped a new HD, created an OSX partition to occupy half of it, left the remainder as MT space, installed OSX, installed  rEFIt, then told Ubuntu to install into MT space. 

I did not check hashes on the distribution; don't know how. I will download and burn again.

I used 'advanced' button, installed Grub to /dev/sda3 as instructed by this webpage:
<https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation> (Actually, the options displayed specified sda, no option for '3' or any other number.)

Thanks for your help, iShurtugal.

<mm>
To check a hash in OS X, in a terminal type
```
md5 filename.iso
```and you'll get something like

```
MD5(filename.iso)= 20665acd5f59a8e22275c78e1490dcc7
```

the numbers after the = sign need to be checked against the hashes on [this page]("https://help.ubuntu.com/community/UbuntuHashes") If they match, the download is good, if they don't, redownload.  I learned the hard way, make sure you learn from my mistake.

---

### Post by modelmaker on 2010-08-07
> **iShurtugal said:**
> To check a hash in OS X, in a terminal type
```
md5 filename.iso
```and you'll get something like

```
MD5(filename.iso)= 20665acd5f59a8e22275c78e1490dcc7
```

the numbers after the = sign need to be checked against the hashes on [this page]("https://help.ubuntu.com/community/UbuntuHashes") If they match, the download is good, if they don't, redownload.  I learned the hard way, make sure you learn from my mistake.

Following your initial suggestion, I've downloaded and burned a new Ubuntu CD. Your second post enabled me to verify the hashes. The distribution is OK. (And my education continues...)

Thanks, iShurtugal

<mm>

---

### Post by modelmaker on 2010-08-07
> **conundrumx said:**
> Installing GRUB to the MBR (/dev/sda) is a recipe for pain.  The Ubuntu installer won't let you install to /dev/sda# if you're doing the entire setup straight from the installer itself, because none of the partitioning is actually done until you hit "go."

To get around this, I used (G)parted to create the Linux partition layout I wanted, then ran the installer and reformatted the ext4 root partition.  I would also strongly advise you have OSX take the entire disk, then use Boot Camp Assistant to resize.  When you finish, select "Quit" instead of "Reboot and Install."  This is the "correct" way to set your Mac up to boot a legacy (aka, BIOS expecting) OS.

I should just edit that wiki with new information, at the rate I've been posting this...

I understand from these comments/suggestions that the installer option to write system and swap into MT space, without manually predefining the extents, is deprecated, or broken, and should not be used. (I wonder if this could be fixed&#8230;)

Q: Does the use of Apple's Boot Camp obviate the need for rEFIt and/or Grub? If not, what action is necessary to include boot blocks at the proper location on the HD? 

Thanks, conundrumx

---

### Post by modelmaker on 2010-08-07
> **alphonce said:**
> I recently installed ubuntu on my imac and heres the way i did it.

first I installed macosx and used disc utility to create 2 partitions, the first with hfs+ for macosx, the other one empty for linux.
then i installed refit.

the i installed ubuntu (lucid 32bit). in the empty space i created first a boot partition (128mb/ext2), then root (/) (15gb) and rest /home (rest), the latter ones ext4.

i installed grub on the boot partition, and everything has worked except one kernel panic, cant mount root vfs.

then i chrooted the linux partitions from the install-cd and just reinstalled grub on the boot partition.

im very new with linux on a mac and just hopes this gives you some help, good luck =)

Could you please clarify "in the empty space i created first a boot partition (128mb/ext2), then root (/) (15gb) and rest /home (rest), the latter ones ext4." I understand boot (128mb/ext2) and root (15gb) (Ext3, I expect) but am unsure about /home and Ext4. Did you create a separate partition for the home directories? 

Also, what does this mean "chrooted the linux partitions"? I've got a huge Ubuntu book, over 1200 pages, haven't found any reference to this. Is there another name for the procedure? 

Thanks for your help, alphonce.** **

---

### Post by conundrumx on 2010-08-09
> **modelmaker said:**
> I understand from these comments/suggestions that the installer option to write system and swap into MT space, without manually predefining the extents, is deprecated, or broken, and should not be used. (I wonder if this could be fixed&#8230;)

Q: Does the use of Apple's Boot Camp obviate the need for rEFIt and/or Grub? If not, what action is necessary to include boot blocks at the proper location on the HD? 

Thanks, conundrumx

rEFIt is a smart, EFI compatible boot device selector.  It hands off the boot process to EFI and says "this is OSX" or "this is legacy (BIOS)."  There is a built in function for this on all Macs, rEFIt just does it better and is much more configurable.

GRUB is a boot loader, it tells the system (on a Mac, the BIOS emulator on top of EFI) how to load the Linux kernel.

These are two very different (though seemingly similar) applications, and while you could go without rEFIt, you need GRUB to load Linux.

Installing GRUB on the MBR puts some odd things into place which I honestly do not fully understand.  In essence, GRUB tries to be the boot loader for the entire system, and rEFIt gets confused.  The Ubuntu installer won't let you install GRUB to a partition that is not formatted **before** the installer starts.  My solution to this is to partition and format the unused space destined for Linux before running the installer.

Using Boot Camp Assistant, I believes, blesses the designated disk space as legacy bootable.  This just makes the boot process faster and cleaner.

Please stop using "MT" for "empty."

Steps:

1. Clean, full disk OSX install.
2. rEFIt install
3. Boot Camp Assistant.  Quit, don't reboot and install.
4. Boot Ubuntu, crate your swap and any other partitions, make sure to format accordingly.
5. Run the Ubuntu installer.  Use manual partitioning to reformat your ext2/3/4 partitions.
6. When you reach the final step for the installer, select advanced and designate your root partition (mounted as /) as the destination for GRUB.  (e.g. /dev/sda4)
7. ???
8. When you reboot, rEFIt should have an OSX and Linux option, both should work as expected.

---

### Post by modelmaker on 2010-08-09
> **conundrumx said:**
> rEFIt is a smart, EFI compatible boot device selector.  It hands off the boot process to EFI and says &quot;this is OSX&quot; or &quot;this is legacy (BIOS).&quot;  There is a built in function for this on all Macs, rEFIt just does it better and is much more configurable.

GRUB is a boot loader, it tells the system (on a Mac, the BIOS emulator on top of EFI) how to load the Linux kernel.

These are two very different (though seemingly similar) applications, and while you could go without rEFIt, you need GRUB to load Linux.

Installing GRUB on the MBR puts some odd things into place which I honestly do not fully understand.  In essence, GRUB tries to be the boot loader for the entire system, and rEFIt gets confused.  The Ubuntu installer won't let you install GRUB to a partition that is not formatted **before** the installer starts.  My solution to this is to partition and format the unused space destined for Linux before running the installer.

Using Boot Camp Assistant, I believes, blesses the designated disk space as legacy bootable.  This just makes the boot process faster and cleaner.

Please stop using &quot;MT&quot; for &quot;empty.&quot;

Steps:

1. Clean, full disk OSX install.
2. rEFIt install
3. Boot Camp Assistant.  Quit, don't reboot and install.
4. Boot Ubuntu, crate your swap and any other partitions, make sure to format accordingly.
5. Run the Ubuntu installer.  Use manual partitioning to reformat your ext2/3/4 partitions.
6. When you reach the final step for the installer, select advanced and designate your root partition (mounted as /) as the destination for GRUB.  (e.g. /dev/sda4)
7. ???
8. When you reboot, rEFIt should have an OSX and Linux option, both should work as expected.

 I may be dumb, but not uneducable. Ubuntu is installed and working. Following the good advice offered here, and a lot of reading, I wiped the drive, reinstalled OSX, shrunk it and added a Windows partition with Boot Camp, deleted that with gparted, created a '/Boot' '/' '/Swap', installed with advanced-grub, used rEFIt to sync, and removed power.   After all that, all I got was a grayed out penguin. Two more boot attempts produced the same grayed out penguin. Went to bed. This morning, it booted! I don't know why...  Thanks very much --

---

### Post by conundrumx on 2010-08-09
> **modelmaker said:**
> I may be dumb, but not uneducable. Ubuntu is installed and working. Following the good advice offered here, and a lot of reading, I wiped the drive, reinstalled OSX, shrunk it and added a Windows partition with Boot Camp, deleted that with gparted, created a '/Boot' '/' '/Swap', installed with advanced-grub, used rEFIt to sync, and removed power.   After all that, all I got was a grayed out penguin. Two more boot attempts produced the same grayed out penguin. Went to bed. This morning, it booted! I don't know why...  Thanks very much --

A legacy boot can take up to 20 seconds, though it often will not.

---

### Post by modelmaker on 2010-08-09
> **conundrumx said:**
> A legacy boot can take up to 20 seconds, though it often will not.

 First the grayed Mr. Tux, then a black screen, then some text from Grub, then some more black and then the Ubuntu logo. Total time about 40 seconds, I'm guessing.

---

### Post by conundrumx on 2010-08-09
> **modelmaker said:**
> First the grayed Mr. Tux, then a black screen, then some text from Grub, then some more black and then the Ubuntu logo. Total time about 40 seconds, I'm guessing.

When I say "a legacy boot" I mean the time it takes the EFI system to understand it's supposed to start BIOS emulation.  So the 20 seconds is the time from selecting Linux to when GRUB actually loads and starts booting Linux.

You can accelerate this by blessing the partition you mount as /boot or /.  You can do this with the [bless]("http://developer.apple.com/mac/library/documentation/Darwin/Reference/ManPages/man8/bless.8.html") command, but I don't recall the exact syntax.

---

