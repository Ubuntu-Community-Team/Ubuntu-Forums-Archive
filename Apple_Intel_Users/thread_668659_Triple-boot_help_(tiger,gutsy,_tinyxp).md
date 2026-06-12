---
title: "Triple-boot help (tiger,gutsy, tinyxp)"
date: 2008-01-15
forum: Apple Intel Users
---

### Post by skullmunky on 2008-01-15
computer: Macbook pro 80GB HD
goal: osx 10.4, ubuntu gutsy, tinyxp beast edition (or other tinyxp ... )

problems:
1. after installing ubuntu, when i boot it i just get a black screen after "loading grub".  looks like it's shut down, even.
2. after installing tinyxp, get "hal.dll corrupt or missing" error

history:

partitioned the HD from terminal in OSX using diskutil - 56 gb for osx, 12 for linux, 12 for windows

installed refit

tried to install tinyxp; bad install disk - won't boot. phooey.

installed ubuntu on /dev/disk0s3 , everything nice and easy.

rebooting into ubuntu: can select it from refit, "loading grub" appears, then black screen and nothing.

meanwhile, made new tinyxp installer.  this one boot.

tried to install on /dev/disk0s4

clever mr. windows installer doesn't think it's formatted, and can't format it because there are already three formatted partitions.  so, deleted partitions /dev/disk0s3 and /dev/disk0s4, created new FAT32 partition, 12 GB on /dev/disk0s3, (supposedly), and installed tinyxp.

tinyxp won't boot - hal.dll is corrupt or missing.

anything obvious i missed or should i start over?  if so : -how- do i start over?  i'd like to not reformat my osx partition if possible...

odd: here's what diskutil list gives me now:

   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *74.5 GB  disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Macintosh HD       50.0 GB   disk0s2
   3:                    EFI                    12.0 GB   disk0s3
   4:   Microsoft Basic Data                    12.2 GB   disk0s4

i thought the windows installer removed partitions 3 and 4 and made a new one on 3.  is that why xp's not booting?  tell me if this is a good plan:

1. /dev/disk0s3 and disk0s4 with diskutil in osx.
2. re-install tinyxp, let it make an "E" partition to install on  (btw is that right?  it shouldn't go on "C", that's the 200MB EFI partition, correct?)

3. then install ubuntu, resizing the xp partition during the install

---

### Post by cyberdork33 on 2008-01-15
try this for the hal.dll issue:
[http://ubuntuforums.org/showthread.php?t=327386](http://ubuntuforums.org/showthread.php?t=327386)

---

### Post by skullmunky on 2008-01-16
thanks, that looks easy enough to solve.  But, new problem: can't mount the windows partition at all!

i formatted it as FAT32 because it's only 12 GB and was hoping to have easier access to the partition from osx and linux. 

in osx, it won't mount; Disk Utility is aware of its existence but won't mount it - i click "mount" and nothing happens, and where the heck is the kernel log in darwin anyway?  

from the ubuntu live cd: lsparts doesn't seem to exist, and synaptic can't find it.
fdisk -l shows nothing.

but, the Partition Editor tells me this:

/dev/sda1   fat32  200MB  boot
/dev/sda2   hfs+  50GiB
unallocated 128 MB
/dev/sda3   unknown  12GiB  boot
/dev/sda4   unknown  12.21GiB

well, I thought that /dev/sda3 was the one I put windows on.  so,

sudo mkdir /mnt/windows
sudo mount -t vfat /dev/sda3 /mnt/windows

mount: wrong fs type, etc.

dmesg: FAT: bogus number of reserved sectors

I feel like I ought to removed sda3 and sda4 and start over.  If I delete those two partitions and remake them in GParted, or even just make one /dev/sda3 for windoze right now and resize later for linux, will that work?  or do I have to manipulate the partitions from osx?  i'm not totally clear on which partitioning tools play nice together in this scenario.

---

### Post by cyberdork33 on 2008-01-16
> **skullmunky said:**
>  but, the Partition Editor tells me this:

/dev/sda1   fat32  200MB  boot
/dev/sda2   hfs+  50GiB
unallocated 128 MB
/dev/sda3   unknown  12GiB  boot
/dev/sda4   unknown  12.21GiB

First, please use the code tags to format your command output, etc so that it is easier to read.

> **skullmunky said:**
> from the ubuntu live cd: lsparts doesn't seem to exist, and synaptic can't find it.
I have never even heard of this command... 

> **skullmunky said:**
> fdisk -l shows nothing.
fdisk is only capable of reading the MBR and not the 'real' GPT. So, you must be very careful with this utility. Since it shows nothing, it sounds like you might be having issues between the EFI partition table (GPT) and the emulated old-style ms-dos partition table in the MBR. if you do not have rEFIt installed, install it (in OSX), then use the partition tool (or whatever it is called in the boot menu) to sync the tables if they are not synced already.

> **skullmunky said:**
> I feel like I ought to removed sda3 and sda4 and start over.  If I delete those two partitions and remake them in GParted, or even just make one /dev/sda3 for windoze right now and resize later for linux, will that work?  or do I have to manipulate the partitions from osx?  i'm not totally clear on which partitioning tools play nice together in this scenario.

Windows likes to be the last partition on the MBR partition table (which has a max of four), so if you do delete the current partitions, keep that in mind.

parted (and thus gparted) is capable of reading and updating the GPT. To get an accurate description of your partitioning scenario, use the following commands:
To get the MBR table:
```
sudo fdisk -l /dev/sda
```to get the GPT:
```
sudo parted list
```

---

### Post by skullmunky on 2008-04-16
Hi, back at work on this triple-boot setup after some months spent on more interesting things :) 

Where I am now: I have Ubuntu installed and running well, and still working on the XP install.  Here's what my partitions are like:

sda1 : EFI
sda2: HFS+, OSX Tiger
sda3: FAT32, TinyXP Beast
sda4: ext3, Ubuntu 7.10
sda5: swap

I get the HAL.DLL error when trying to boot XP.  I read through the threads about fixing this by editing BOOT.INI, but it was already set to partition 3:

```

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

just for kicks I tried setting it other partitions like 4, 2, etc, but no improvement.  I put it back to 3 and now when I select "Microsoft Windows XP Professional" from the windows bootloader it just restarts.

Oops now when I boot into ubuntu I get a kernel panic:

```

MP-BIOS Bug: 8254 timer not connected to IO-APIC

```

well, that's a digression.  heh heh.

When I installed TinyXP, it did not give me the option to format the partition.  I know this is supposed to be necessary for some reason because boot camp can't format things properly, or something (?), but the answer file in tiny xp removes the formatting option.  I found (and lost) some instructions on how to modify the xp installer disk to remove the answer file (using linux) - anyone know where that is?

---

