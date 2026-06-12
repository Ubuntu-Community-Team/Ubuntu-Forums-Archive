---
title: "How to Install multiple linux versions"
date: 2007-12-10
forum: Apple Intel Users
---

### Post by hardawayd on 2007-12-10
I am having trouble installing multiple linux versions on my new MBP. I successfully installed Gusty but when i installed Linux Mint both Gusty and Linux Mint will not launch when I select them from the erift menu. The screen says loading stage 2.. and just hangs there. I have been unable to find any help.  Everyone seems to be triple booting in Mac OS, Windoz and Linux whereas I would like to have Mac OS and several Linuxes instead. Any help would be appreciated.

---

### Post by cyberdork33 on 2007-12-10
> **hardawayd said:**
> I am having trouble installing multiple linux versions on my new MBP. I successfully installed Gusty but when i installed Linux Mint both Gusty and Linux Mint will not launch when I select them from the erift menu. The screen says loading stage 2.. and just hangs there. I have been unable to find any help.  Everyone seems to be triple booting in Mac OS, Windoz and Linux whereas I would like to have Mac OS and several Linuxes instead. Any help would be appreciated.
Please post the out put of the following commands:

```
sudo fdisk -l /dev/sda
```
```
sudo parted /dev/sda print
```

and please post the contents of the menu.lst file for grub.

---

### Post by hardawayd on 2007-12-10
mint@mint:~$ sudo fdisk -l /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00002880

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        8002    64063464   af  Unknown
/dev/sda3   *        8002       11649    29296875+  83  Linux
/dev/sda4           11649       14466    22628906+  83  Linux
mint@mint:~$
mint@mint:~$ sudo parted /dev/sda print

Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI system partition  boot
 2      210MB   65.8GB  65.6GB  hfs+         Customer                  
 3      65.8GB  95.8GB  30.0GB  ext3                               boot




 4      95.8GB  119GB   23.2GB  ext3                               boot
 5      119GB   120GB   1051MB  linux-swap                             

Information: Don't forget to update /etc/fstab, if necessary.            

mint@mint:~$

---

### Post by cyberdork33 on 2007-12-10
well, your partitions look good from what I can tell, and most of your menu.lst looks right, but you are using the same UUID for both partitions in your menu.lst. This cannot be right.

Try changing the root= parameter on the kernel line to the block device rather than the UUID, like this:
```
root=/dev/sda3
```and
```
root=/dev/sda4
```
This may not completely fix the problem, but I would try that before anything else.

---

### Post by hardawayd on 2007-12-10
I tried changing the root to /dev/sda3 etc. but no good.  There are a few other things I am not sure about.  below you can see that the efi listing doesn not show my partitions 3 and 4 to be linux. Is this a problem? Also, when I boot it shows three Linux icons instead of two. I am wondering if the refit files are out of sync with the disk some how. How do get rid of the extra penguin icon at boot time? Any ideas?  Do I need boot camp---i thought it was only needed if you install windoz but i really don't know?


csbmgrs-macbook-pro:~ hardaway$ sudo diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *111.8 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            61.1 Gi    disk0s2
   3:                        EFI                         27.9 Gi    disk0s3
   4:       Microsoft Basic Data                         9.3 Gi     disk0s4
csbmgrs-macbook-pro:~ hardaway$

---

### Post by cyberdork33 on 2007-12-10
you do not need bootcamp. All that bootcamp does is partition the disk.

it is normal that EFI sees your linux partitions as Microsoft data... It is strange that it shows one as being EFI though. Though it looks as though it is recognized properly with parted (which reads the EFI partition table). diskutil seems to be completely missing the swap partition too.

In rEFIt, there is an option to sync the partition tables. You should run that to see if they are out of sync (it will ask before making any changes).

You have 3 linux icons, likely because refit sees 3 different linux OS options. It sees both linux partitions as bootable for some reason, and then there is also grub in the MBR.

What tools have you been using to mess with the partitions?

---

### Post by hardawayd on 2007-12-10
I have only used the partition tool in the Linux distro for making my partitions.  The one in the MBR makes sense since i remember making that mistake during one of my many installs. Is there a way to redo the MBR to get rid of it?

---

### Post by cyberdork33 on 2007-12-10
> **hardawayd said:**
> I have only used the partition tool in the Linux distro for making my partitions.  The one in the MBR makes sense since i remember making that mistake during one of my many installs. Is there a way to redo the MBR to get rid of it?
yes, but what tools? some tools do not support GPT, and thus you can get problems.

---

### Post by hardawayd on 2007-12-10
not sure but i think ubuntu uses gparted.

---

### Post by cyberdork33 on 2007-12-11
> **hardawayd said:**
> not sure but i think ubuntu uses gparted.
yes, it does... but it did not always support GPT. Which version of linux mint did you install?

Did you check the partition tool in rEFIt?

---

### Post by hardawayd on 2007-12-12
1. Linux Mint 4.0
2. I did check the partition tool in refit--it said everything is synced
3. i had gusty in partition 3, mint in part 4 and even tried gusty again in part 5.

Only Mac would boot---the others just had a screen that said GRUB and stalled out.

Then I booted with the latest systemrescuecd and deleted partitions 4 and 5.  Now with only the original install of refit, mac os and gusty my MBP boots as before.  I had to resync after deleting parts 4 and 5 though.

it appears that there is some kind of confusion between when to use mbr vs gpt if that makes sense. I would still like to get several other linux distros to work.  Why don't the ubuntu engineers make a version of linux that works with gpt/efi?

---

### Post by cyberdork33 on 2007-12-12
> **hardawayd said:**
> 1. Linux Mint 4.0
2. I did check the partition tool in refit--it said everything is synced
3. i had gusty in partition 3, mint in part 4 and even tried gusty again in part 5.

Only Mac would boot---the others just had a screen that said GRUB and stalled out.

Then I booted with the latest systemrescuecd and deleted partitions 4 and 5.  Now with only the original install of refit, mac os and gusty my MBP boots as before.  I had to resync after deleting parts 4 and 5 though.

it appears that there is some kind of confusion between when to use mbr vs gpt if that makes sense. I would still like to get several other linux distros to work.  Why don't the ubuntu engineers make a version of linux that works with gpt/efi?Ubuntu does work with GPT EFI, otherwise you couldn't run it at all...

Linux Mint 4 should work just as well as gutsy (since it is essentially the same) unless they use a different partitioner.

Here is what I would try, as it seems like grub is what is acting funny...

1. start Ubuntu Live CD
2. start the partition editor from the admin menu. Create your 2 root partitions and swap (note, you must make sure that the root partitions are <=4 otherwise you may have problems booting. You should end up with a partition scheme similar to what you had already.
3. start the Ubuntu installer. Choose manual partitioning and set all the partition mount points (you can format the root partitions here if you want, but it shouldn't matter). Make sure it does not attempt to mount the EFI partition. When you continue, you might get an error about 'fats don't match' but just ignore it. It is an issue with the EFI partition format.
4. on the last screen before it actually starts to install, click the "Advanced" button. In here you can specify the location to install Grub. Install grub to the Ubuntu root partition (not the MBR) which should be something like (hd0,2) if you are installing  in the same manner as you did before.
5. after the install finishes, you should have a linux icon in rEFIt for gutsy and it should work.
6. start the install for Linux Mint. I am unsure of the specifics of this OS, but it should install grub to the MBR by default. This is what you want. after installing you should have two linux icons in rEFIt, one for each partition. 

I cannot verify that this will absolutely work, but I think it is worth a try. Sharing the same menu.lst to boot more than one Linux version can get messy and it is best to keep them separate.

---

### Post by hardawayd on 2007-12-12
One problem is that i am using the alternatvie gusty-64 disk---it does not have an advanced option to direct where to put grub.  It had been recommended on other threads to use the alternative one instead of the desktop version.  Also, i have read that it is better to install ubuntu after partition 4 so that the MBR is not used.  What is your thinking on that?

---

### Post by cyberdork33 on 2007-12-12
> **hardawayd said:**
> One problem is that i am using the alternatvie gusty-64 disk---it does not have an advanced option to direct where to put grub.  It had been recommended on other threads to use the alternative one instead of the desktop version.  Also, i have read that it is better to install ubuntu after partition 4 so that the MBR is not used.  What is your thinking on that?
Not everyone has a bootable system if you install after 4. Maybe that has changed, but at least that is how it used to be. 

I think there is a way to specify the location for grub on the alt disc too, but I can't remember where it is. (It has been too long). Both the Live and alt cd works fine though.

---

