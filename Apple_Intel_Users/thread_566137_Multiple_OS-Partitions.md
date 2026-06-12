---
title: "Multiple OS-Partitions ?"
date: 2007-10-03
forum: Apple Intel Users
---

### Post by karl_kashofer on 2007-10-03
Hi !

I am a firsttime MacBook owner, and finally (after the recent firmware update that fixed the keyboard in GRUB) am getting most things I need working.

However, on my last laptop and my desktop I usually make a 5GB boot partition with a text-mode linux install and several 20GB partitions. Into the 20GB partitions I can then install several linux versions with their separate GRUB installed into the partition. I then install grub into the hdd mbr to boot from the 5GB partition, in there I have static boot stanzas which use chainloading to load the GRUB in the 20GB partitions which then load the system in the partition. This allows me to select from the first GRUB menu which system to boot, and each of the 20GB systems is completely independent of the others, kernel updates and menu.lst updates are never interfering with each other. My data is then stored on a large partition from the rest of the hdd which gets mounted onto /home.

Now on the macbook we have the GPT/MBR issue, and I am hoping someone in here can find a solution to this problem. I want to keep the OSX partition, mainly to be able to do firmware updates.

AFAIK we can only have 4 Partitions as long as I want to keep the OSX system unchanged. Having the EFI, OSX partition that leaves one for swap, and one for a linux system.

I am not sure if it would be possible to have more mbr partitions, thus un-synching the GPT and MBR. If it is not strictly necessary to have them synced, maybe one could then make several more MBR partitions for more linux systems. However, I suspect only the first two primaries would be bootable from rEFIt.

Now someone in another thread suggested that it might be possible to boot from this one partition and then very early in the boot process switch (chroot?) to the other partitions. He suggested that as soon as we can boot a linux kernel we can basically re-boot into any other partition.

So these are my questions:

Do you think that its possible to have more partitions without loosing bootability of the linux partition ?
Can we really switch from one partition to another (including changed kernel) after boot ?

Would be nice to be able to play around with several systems,
Thanks,
Karl

---

### Post by cyberdork33 on 2007-10-03
> **karl_kashofer said:**
> However, on my last laptop and my desktop I usually make a 5GB boot partition with a text-mode linux install and several 20GB partitions. Into the 20GB partitions I can then install several linux versions with their separate GRUB installed into the partition. I then install grub into the hdd mbr to boot from the 5GB partition, in there I have static boot stanzas which use chainloading to load the GRUB in the 20GB partitions which then load the system in the partition. This allows me to select from the first GRUB menu which system to boot, and each of the 20GB systems is completely independent of the others, kernel updates and menu.lst updates are never interfering with each other. My data is then stored on a large partition from the rest of the hdd which gets mounted onto /home.

Now on the macbook we have the GPT/MBR issue, and I am hoping someone in here can find a solution to this problem. I want to keep the OSX partition, mainly to be able to do firmware updates.

AFAIK we can only have 4 Partitions as long as I want to keep the OSX system unchanged. Having the EFI, OSX partition that leaves one for swap, and one for a linux system.
Interrupting here to give some advice, and tweak what you have said a bit. 
First, 5GB is WAY too big for what you are doing with that 'boot' partition. try something like 100MB or even less if you do not need to store kernels on it. Also, you might not even need this for your Mac as you can use rEFIt which basically does what you just said.
Second, OSX does not have to be one of the first four partitions, and neither does swap. I have also seen some people have success with Linux beyond the 4th partiton as long as grub is installed on one of the first 4. Linux can access the GPT disk partitions just fine (including mounting home, swap, whatever), the issue lies in booting a legacy OS with the BIOS emulation that Apple has provided.

> I am not sure if it would be possible to have more mbr partitions, thus un-synching the GPT and MBR. If it is not strictly necessary to have them synced, maybe one could then make several more MBR partitions for more linux systems. However, I suspect only the first two primaries would be bootable from rEFIt. You have to realize that there are no _real_ MBR partitions on the system, they are all GPT partitions. The BIOS emulation just sees the first 4 (whenever you sync) as the MBR partitions on the disk. There is no way to emulate 'extended' or 'logical' partitions. Anyway, no, they are not required to be in sync, sort of, but that is a tricky thing to mess with, but you can get some interesting results. See this: [http://forum.onmac.net/showthread.php?t=2793](http://forum.onmac.net/showthread.php?t=2793)

> Now someone in another thread suggested that it might be possible to boot from this one partition and then very early in the boot process switch (chroot?) to the other partitions. He suggested that as soon as we can boot a linux kernel we can basically re-boot into any other partition.

So these are my questions:

Do you think that its possible to have more partitions without loosing bootability of the linux partition?Yes. In fact you may be able to have several bootable linux partitions if you can use a method like in the link above
> Can we really switch from one partition to another (including changed kernel) after boot ?Although I have no idea how to do it, once a kernel is loaded, you can access any partition on the GPT disk (because linux can read the GPT), and there is the ability in newer kernels to replace itself with another kernel without rebooting. So, in this manner, I could see something like this working. You would basically have a very small linux system that only loaded another linux system (that you select somehow).

---

### Post by pxwpxw on 2007-10-03
**karl_kashofer**

Here is a grub trick you may not have noticed, that may be easier than switching kernels or using chainloader and achieve the same result as far as booting is concerned. Only one grub bootloader is needed and the other linux partitions are not restricted to mbr primary range.

With one master grub loader and menu it is possible to load local menus from other linux partitions anywhere on the disk, using the "configfile" term. So local  configuration changes and updates would not need any change to the master grub menu.

For example this would be master grub menu entry for one linux root system at sda8:
```

title linuxsda8
 root (hd0,7)
 configfile /boot/grub/menu.lst

```
# the configfile command then loads and displays the remote menu from the 
# root at hd(0,7)= /dev/sda8 with its selectable  local options and kernel names.
=====================

---

### Post by cyberdork33 on 2007-10-03
> **pxwpxw said:**
> **karl_kashofer**

Here is a grub trick you may not have noticed, that may be easier than switching kernels or using chainloader and achieve the same result as far as booting is concerned. Only one grub bootloader is needed and the other linux partitions are not restricted to mbr primary range.

With one master grub loader and menu it is possible to load local menus from other linux partitions anywhere on the disk, using the "configfile" term. So local  configuration changes and updates would not need any change to the master grub menu.

For example this would be master grub menu entry for one linux root system at sda8:
```

title linuxsda8
 root (hd0,7)
 configfile /boot/grub/menu.lst

```# the configfile command then loads and displays the remote menu from the 
# root at hd(0,7)= /dev/sda8 with its selectable  local options and kernel names.
=====================
Keep in mind this assumes grub can read the contents of a partition beyond #4 (if it can even see them)

---

### Post by pxwpxw on 2007-10-04
> **cyberdork33 said:**
> Keep in mind this assumes grub can read the contents of a partition beyond #4 (if it can even see them)

Here you are, do it all the time in PC land, no problem.

OSX, XP, 2 Linux, refit.

Booting from refit or from Apple Icon, to grub on sda3, xubuntu704 / menu1
to menu2 and kernel on sda8, then 
from menu2 select kernel and mount root system back at sda3 (dont have a root system on sda8 just now, just  /boot/grub/ with kernel and grub files.)

Can post more if you want.

Partitions: 
(just what I happen to have, not related to OP issue)
```

root@ubuntu:/home/admax# gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     39222871  Mac OS X HFS+
 3       39485016     56263263  Basic Data   -----linux1 menu1
 4       56525408     81530047  MS Reserved  --- XP
 5      152395204    156301454  Linux Swap
 6      148437500    152395203  Mac OS X HFS+ --- REFIT
 7      131443904    148437499  MS Reserved
 8       81530048    104989888  Basic Data    ---- linux2 menu2

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     39222871  af  Mac OS X HFS+
 3 *     39485016     56263263  83  Linux
 4       56525408     81530047  0b  FAT32

Status: Tables are synchronized, no need to sync.

root@ubuntu:/home/admax# 

root@ubuntu:/home/admax# parted /dev/sda
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) P                                                                

Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags  
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot   
 2      210MB   20.1GB  19.9GB  hfs+         Apple_HFS_Untitled_1         
 3      20.2GB  28.8GB  8590MB  ext3         uxroot1                      
 4      28.9GB  41.7GB  12.8GB  fat32        XP                    msftres
 8      41.7GB  53.8GB  12.0GB  ext3                                      
 7      67.3GB  76.0GB  8701MB  fat32                              msftres
 6      76.0GB  78.0GB  2026MB  hfs+                               hidden 
 5      78.0GB  80.0GB  2000MB  linux-swap                                

(parted)    

```

---

