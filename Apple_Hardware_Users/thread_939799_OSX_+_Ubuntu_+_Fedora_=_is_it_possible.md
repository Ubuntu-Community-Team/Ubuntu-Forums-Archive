---
title: "OSX + Ubuntu + Fedora = is it possible ?"
date: 2008-10-06
forum: Apple Hardware Users
---

### Post by alinux on 2008-10-06
Hello All,

I've Macbook 3.1 Gen.
I need to have 2 linux distros on my hard disk + a DATA partition.
Something like:


1 partition  | 2 partition | 3 partition | 4 partition | 5 partition | 6 par
rEFIt          OSX           DATA(FAT32)   Ubuntu        Fedora       SWAP


Is it possibile ?

---

### Post by cyberdork33 on 2008-10-06
> **alinux said:**
> Hello All,

I've Macbook 3.1 Gen.
I need to have 2 linux distros on my hard disk + a DATA partition.
Something like:


1 partition  | 2 partition | 3 partition | 4 partition | 5 partition | 6 par
rEFIt          OSX           DATA(FAT32)   Ubuntu        Fedora       SWAP


Is it possibile ?
Not like that. You could do:
1. EFI
2. Ubuntu
3. Fedora
4. Data
5. OS X
6. swap

---

### Post by alinux on 2008-10-06
> **cyberdork33 said:**
> Not like that. You could do:
1. EFI
2. Ubuntu
3. Fedora
4. Data
5. OS X
6. swap



So you mean that I sohuld reinstall everything ?

Actually my stuation is:
1.EFI
2.OSX
3.DATA
4.Fedora
5.Ubuntu
 no swap

And rEFIt sees only OSX and Fedora...
If I try to recync, it rEFit tells me that there is nothing to sync.


P.S Once I have a new 320 GB HD, for my Mackbook, in which sequence 
should I install them?

1.EFI, then Ubuntu, then Fedora, +DATA(FAT), then OSX then SWAP ?
or
1.EFI, then OSX, +DATA(FAT), then Ubuntu, then Fedora

---

### Post by Sponzenbroekske on 2008-10-06
I have no idea what EFI is but anywho.

You can have 4 primary partitions, those are gonna be OSX, fedora, ubuntu and data, swap can be an extended (logical) partion of ubuntu or fedora, and EFI.....

I would first download gparted livecd, and partition my harddrive, with 2 ext3, 1 FAT32 and 1 OSX (dont know what it uses), then I would install OSX, then fedora and ubuntu( or ubuntu and fedora).

---

### Post by cyberdork33 on 2008-10-06
> **alinux said:**
> So you mean that I sohuld reinstall everything ?

.. rEFIt sees only OSX and Fedora...
because everything else is beyond the fourth partition.
> **alinux said:**
> If I try to recync, it rEFit tells me that there is nothing to sync.because there is nothing to sync. It can only sync the first four partitions...
> **alinux said:**
> P.S Once I have a new 320 GB HD, for my Mackbook, in which sequence 
should I install them?

1.EFI, then Ubuntu, then Fedora, +DATA(FAT), then OSX then SWAP ?
or
1.EFI, then OSX, +DATA(FAT), then Ubuntu, then Fedora

The problem is that only the first four partitions can contain bootable 'legacy' operating systems, and one of those four are taken up by the EFI partition. OSX is not a 'legacy' operating system so it does not need to be one of the first 4.

Actually, if you data partition is not going to be bootable (no windows or anything like that), then you can put is after the first 4 as well...

1. EFI
2. OSX
3. Ubuntu
4. Fedora
5. Data
6. swap

> **Sponzenbroekske said:**
> I have no idea what EFI is but anywho.

You can have 4 primary partitions, those are gonna be OSX, fedora, ubuntu and data, swap can be an extended (logical) partion of ubuntu or fedora, and EFI.....On Intel Macs, there is an EFI partition about 200MB in size at the beginning of the disc. removing it means no firmware updates for your mac.

---

### Post by Seq on 2008-10-06
You didn't specify two things: (1) The order of OS install, not just partition layout (I'm assuming you installed Fedora after Ubuntu), and (2) Grub install location (Fedora uses Grub, right?).

By default, both Fedora and Ubuntu will install Grub to the MBR. Refit boots, finds some EFI/OSX partition(s), and a MBR partition. Since you installed Fedora second (again, I'm assuming) the MBR Grub points to the Fedora partition, and bootstraps from there.

I can think of a few things you might want to try:
[LIST=1]
[*]Set up Grub in both Fedora and Ubuntu to install to their Local partitions instead of the MBR. Refit might see two bootable partitions. I only have OSX+Ubuntu right now, but have installed Grub to sda3 instead of MBR and had it show up in Refit properly. (You'd likely have three linuxes show up due to the existing MBR record, you would have to clear this, though I wouldn't worry about it unless the other two work).
[*]Add entries to Fedora's grub config to boot Ubuntu. This is going to be a bit of a pain as it will break when Ubuntu has a kernel update. You could get Ubuntu to install Grub to it's own partition and set up chainloading, but by doing this you will have Ubuntu show up in Refit anyway, and not need any special Fedora config..
[/LIST]

---

### Post by alinux on 2008-10-06
Guys, first of all, thank you for your time!

So I'm going to:
backup my DATA(fat32) partition, and make something like this:

/dev/sda1 EFI
/dev/sda2 OSX
/dev/sda3 Ubuntu with grub on /dev/sda3 (not on MBR)
/dev/sda4 Fedora with grub on /dev/sda4 (not on MBR)
/dev/sda5 1GB SWAP space
/dev/sda6 a big DATA fat32 partition.

Do you like it in this way?

And what about boootable flags? In this way which one should have a bootable flag?

---

### Post by cyberdork33 on 2008-10-06
> **alinux said:**
> Guys, first of all, thank you for your time!

So I'm going to:
backup my DATA(fat32) partition, and make something like this:

/dev/sda1 EFI
/dev/sda2 OSX
/dev/sda3 Ubuntu with grub on /dev/sda3 (not on MBR)
/dev/sda4 Fedora with grub on /dev/sda4 (not on MBR)
/dev/sda5 1GB SWAP space
/dev/sda6 a big DATA fat32 partition.

Do you like it in this way?That should work, assuming you install the bootloaders to the root partition.

> **alinux said:**
> And what about boootable flags? In this way which one should have a bootable flag?
Create partitions for everything initially with DiskUtility in the OS X installer. Don't worry about the format as you can change it to the correct format when you install linux.
DiskUtility will set the boot flag appropriately in the GPT (and don't change it because it will mess stuff up).
The installers for your two linux distros should set the boot flag on the MBR side appropriately.

---

### Post by alinux on 2008-10-06
> **cyberdork33 said:**
> That should work, assuming you install the bootloaders to the root partition.


Create partitions for everything initially with DiskUtility in the OS X installer. Don't worry about the format as you can change it to the correct format when you install linux.
DiskUtility will set the boot flag appropriately in the GPT (and don't change it because it will mess stuff up).
The installers for your two linux distros should set the boot flag on the MBR side appropriately.


Ok, I'll try it as soon as possible. Sorry but, what's GTP is ? :confused:

---

### Post by cyberdork33 on 2008-10-06
> **alinux said:**
> Ok, I'll try it as soon as possible. Sorry but, what's GTP is ? :confused:

GUID Partition Table. It is the "real" partitioning method that Intel Macs use. There is also a partition table in the MBR, but it is not the "real" partition table, but only maps 4 partitions to the GPT.

I have a big article about this on my blog that goes into more detail:
[http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/](http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/)

---

### Post by alinux on 2008-10-07
Hello Again,


I've reinstalled OSX (it was my first time OSX installation).
As you said I've made partitions by Disk Utility dividing HD
in 5 parts:

1. OSX HFS
2. some HFS partition (for future Ubuntu)
3. some HFS partition (for future Fedora)
4. 1GB HSF partition (for future SWAP)
5. the rest of HD, FAT32 for DATA.

OSX, installed without problems and it sees all of my partitions.
Now I'm going to install Ubuntu 8.10 (beta).
And I see this:

Please see a atachement.

---

### Post by cyberdork33 on 2008-10-07
> **alinux said:**
> OSX, installed without problems and it sees all of my partitions.
Now I'm going to install Ubuntu 8.10 (beta).
And I see this:

That looks correct. What is the issue? You have gparted on the livecd that you can use to edit the partitions, and you can use the partitioning tool in the installer (what you took a screenshot of) to change the format.

---

### Post by alinux on 2008-10-07
> **cyberdork33 said:**
> That looks correct. What is the issue? You have gparted on the livecd that you can use to edit the partitions, and you can use the partitioning tool in the installer (what you took a screenshot of) to change the format.

I simply don't understand why there are some free MBytes between 
partitions ? (you can see that on the screenshot) Can I resize them to merge into existent partitions?

I think that in this way Disk Utility, wastes almost 1 GB of precious space.
I'm going to reinstall OSX fir first
and recreate again:
1.OSX
2.HFS - for ubuntu
3.HFS - for fedora
4.HFS - swap

5.FAT - dor DATA


Shame that I can't Use Ubuntu partitioner for create linux oriented partitions.
I mean: Install OSX on a manually created partition by OSX. EX 50GB, the rest free space.
Then boot from Ubuntu CD and make other partititons etc etc...

Creating every partition with Disk Utility is really...(miss the word)
not ellegant :)

---

### Post by cyberdork33 on 2008-10-07
> **alinux said:**
> I simply don't understand why there are some free MBytes between 
partitions ? (you can see that on the screenshot) Can I resize them to merge into existent partitions?Yes, DiskUtility does that. Nobody knows why. You can resize.

> **alinux said:**
> I think that in this way Disk Utility, wastes almost 1 GB of precious space.
I'm going to reinstall OSX fir first
and recreate again:
1.OSX
2.HFS - for ubuntu
3.HFS - for fedora
4.HFS - swap

5.FAT - dor DATA


Shame that I can't Use Ubuntu partitioner for create linux oriented partitions.
I mean: Install OSX on a manually created partition by OSX. EX 50GB, the rest free space.
Then boot from Ubuntu CD and make other partititons etc etc...

Creating every partition with Disk Utility is really...(miss the word)
not ellegant :)You can... What I meant by create the partitions for everything up front was to allocate the space... After that, you can Use the Ubuntu partitioner to change around whatever you like. You don't need to reinstall again...

---

### Post by alinux on 2008-10-08
> **cyberdork33 said:**
> Yes, DiskUtility does that. Nobody knows why. You can resize.

You can... What I meant by create the partitions for everything up front was to allocate the space... After that, you can Use the Ubuntu partitioner to change around whatever you like. You don't need to reinstall again...

So if I can use Ubuntu partitioner, I can also use OSX Dsk Utility
to make the first partition for OSX,
and after I can create others with Ubuntu partitioner... or you suggest
NECESSARY use Disk Utility for create all of partitions ?

---

### Post by cyberdork33 on 2008-10-08
> **alinux said:**
> So if I can use Ubuntu partitioner, I can also use OSX Dsk Utility
to make the first partition for OSX,
and after I can create others with Ubuntu partitioner... or you suggest
NECESSARY use Disk Utility for create all of partitions ?
It is better to create your OSX and your data partition with Disk Utility as that will make sure that OS X can see the shared partition.

I usually tell people to create one big partition where you want to have your linux install with Disk Utility just to allocate the space you want, then boot the Ubuntu Live CD and delete that partition and create the partitions you want for linux in its place.

---

