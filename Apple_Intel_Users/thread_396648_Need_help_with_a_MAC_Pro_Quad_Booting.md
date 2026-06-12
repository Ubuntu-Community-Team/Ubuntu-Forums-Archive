---
title: "Need help with a MAC Pro Quad Booting"
date: 2007-03-29
forum: Apple Intel Users
---

### Post by bob2345 on 2007-03-29
I have a MAC Pro with Intel Xeon Processors. I have been trying to get Ubuntu to install on it for a while now with little success. Current Configuration consists on 250GB drive with OSX a 300GB hard drive split with Windows XP on one partition and Vista on the other and I would like to install ubuntu on a 3rd drive 200GB. I've installed rEFIt and can get the windows and MAC partition to boot fine but when I installed Ubuntu I can make it boot it just goes to the Windows boot Loader. The installed of ubuntu appears to take place normally but it will not boot. Any sugestions I'm kind new to this. Thanks for the help.

---

### Post by mflaig on 2007-04-11
I've been working on triple boot with 2 disks for a long time and didn't get it to run at first.

check: macpro.netzblock.org, I've been writing down some things there but discontinued as I got it to run halfway... I have to mention that I wanted Linux to be mirrored (raid1+lvm) with encrypted disks so I had lots and lots of problems and couldn't install feisty (alternate was broken when setting up raid and as I heard it still is)

The weird thing I found is hat MacOS X detected my second harddrive as the first and the first as the second and windows xp does not have to be on the same disk as macos x. But if not it seems you need lilo to boot it. Everything on this machine is really weird.

So the configuration that worked for me was the following

/dev/sda
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26          91      524288   83  Linux
/dev/sda3              91       23589   188743680   fd  Linux raid autodetect
/dev/sda4   *       23589       27505    31457280    b  W95 FAT32

/dev/sdb
  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204819+  ee  EFI GPT
/dev/sdb2              26       23524   188743680   fd  Linux raid autodetect
/dev/sdb3   *       23524       27440    31457280    b  W95 FAT32
/dev/sdb4           27440       30385    23661712   af  Unknown
  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204819+  ee  EFI GPT
/dev/sdb2              26       23524   188743680   fd  Linux raid autodetect
/dev/sdb3   *       23524       27440    31457280    b  W95 FAT32
/dev/sdb4           27440       30385    23661712   af  Unknown

The unknown is actually OSX if I remember correctly. 
FAT 32 does not like more than 32 gb. If you use more than 32 gb you would use an fat extension that linux can handle but OSX won't ...

My opionion: If I reinstall this machine I will kick OSX out and use just Grub or lilo as an boot loader. refit is nice but I really don't use OSX. And: since the first disk (second on osx) has no hfs partition macosx wants to initialize after every bootup. clicking no prevents data loss but that is just not nice :( 

note to myself: Next installation sould be single boot linux. Save yourself a lot of trouble when only dealing with sophisticated operating systems.

Quad booting shouldn't be that of a problem. as long as refit detects the partition and the boot loader.

---

