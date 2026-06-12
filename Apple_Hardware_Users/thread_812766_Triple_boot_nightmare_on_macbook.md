---
title: "Triple boot nightmare on macbook"
date: 2008-05-30
forum: Apple Hardware Users
---

### Post by niteblind on 2008-05-30
Hi All,

Can some please put me out of my misery? I have been trying to triple boot my mac book but cannot seem to get what I want.

I want to have the following partitions on the macbooke

0. mac os x system partition 200mb
1. mac os x 30gb
2. winxp 30gb
3. linux swap 2gb
4. linux root 10gb
5. linux /home 190gb

I have tried using gparted and the diskutility to partition as above and then simply install win XP SP2 to the correct partition but it does not work

Each time I install from a bootable cd it loads the setup utility. formats the partition to either FAT32 or NTFS, copies the windows files, reboots the mac and the cannot go any further and I get one of the following error:

disk error press any keu to restart
missing or corrupt hal.dll
unmountable_boot_volume

So I have tried to use boot camp to install from the OS10.5 desktop. This does not allow me to create more than the one mac partition and the one windows partition on it so what can I do?

I tried setting everything else as free space and it shows the partutions as:

0. mac os x system partition 200mb
1. mac os x 30gb
2. unallocated space 190gb
3. winxp 30gb

I tried installing as these showed with windows using boot camp and all goes fine but AS SOON AS I then install linux it screws up the winsow install.

Can anyone tell me what I am doing wrong? Is there a way to get boot camp to run on a pre partitioned drive as currently it just errors saying it must be all one mac os X partition or be partitioned bu boot camp and I then cannot get it to do the partitioning they way I want.

any help would be massively appreciated

niteblind

---

### Post by cyberdork33 on 2008-05-30
> **niteblind said:**
> I want to have the following partitions on the macbooke

0. mac os x system partition 200mb
1. mac os x 30gb
2. winxp 30gb
3. linux swap 2gb
4. linux root 10gb
5. linux /home 190gb

I have tried using gparted and the diskutility to partition as above and then simply install win XP SP2 to the correct partition but it does not work

Each time I install from a bootable cd it loads the setup utility. formats the partition to either FAT32 or NTFS, copies the windows files, reboots the mac and the cannot go any further and I get one of the following error:

disk error press any keu to restart
missing or corrupt hal.dll
unmountable_boot_volume
Windows likes to be the last partition in the MBR. Do something like:

1. EFI Partition
2. OSX Partition
3. Ubuntu Root Partition /
4. WinXP
5. Linux home /home
6. Linux swap

The easiest way to proceed is to to a complete install of OSX (so you only have the EFI and OSX partitions, then use bootcamp to make a partition equal to the size of all the other partitions you want to make. After that, use gparted to delete the "bootcamp" partition and create your other partitions in it's place. Make sure the partition tables are synced after that, and windows will see itself in the last MBR partition (partition 4).
> **niteblind said:**
> I tried installing as these showed with windows using boot camp and all goes fine but AS SOON AS I then install linux it screws up the winsow install.Additionally, windows has issues if you change something about the partitions after you have already installed. You might be able to recover after that by running 'bootcfg /rebuild' in the windows recovery disc.

---

### Post by ventrinal on 2008-05-30
Dude! You've left me speechless ;-)...that was a really nice one mate….hope we can pull more of this kind.

---

### Post by niteblind on 2008-05-31
Okay in a moment of brilliiance after posting this uesterday I tried the partitions as:

1. EFI Partition
2. OSX Partition
3. Ubuntu Root Partition /
4. WinXP
5. Linux home
6. Swap

It still screwed up after I installed linux but I think this may have been beciase of my making the linux changes after the windows install.

Will try again today making all the partition changes before I install winsows and will let you know how I get on.

niteblind

---

### Post by niteblind on 2008-05-31
Arrrrgh I still cannot get this damned thing working. This is what I have done today what am I doing wrong?

1. Erased the HDD, and then formatted as Mac Extended Journaled 230gb drive.

so at present there are 2 partitions the 200 mb EFI and 230gb Mac OSX.

2. Run Bootcamp and create a winXP 30gb partition.

3. Resized the Mac OSX drive to also be 30gb.

Partitions now:
1 EFI 200mb
2 OSX 30db
3 Unallocated space 170gb
4 win XP 30gb

At this point I then loaded gparted and moved the free space so that it looks like this:

1 EFI 200mb
2 OSX 30db
3 linux /root 30gb
4 win XP 30gb
5 linux /home 136gb
6 linux swap 4gn

so now I think that everything is sorted and load into OSX and try to rn bootcampt but it com not work as it did not partition the drive!!!!!

If I try and install winxo without going directly through boot camp it fails again. anyone know why or what I am doing wrong?

niteblind

---

### Post by niteblind on 2008-06-01
bump :D

---

### Post by niteblind on 2008-06-01
erm hello? anyone?

---

### Post by cyberdork33 on 2008-06-01
there is an extensive installation guide in the Macbook Pro Wiki page. It includes a triple boo install. This has been known to work (and the general install procedure should be the same for all Intel Macs).
[https://help.ubuntu.com/community/MacBookPro#head-8224be4fd9e91b7d57ecb73af7a8a420f002082d](https://help.ubuntu.com/community/MacBookPro#head-8224be4fd9e91b7d57ecb73af7a8a420f002082d)

---

