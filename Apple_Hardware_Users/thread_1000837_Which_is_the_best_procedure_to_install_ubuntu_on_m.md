---
title: "Which is the best procedure to install ubuntu on macbook which already has windows?"
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by naren.bharatwaj on 2008-12-03
Can someone tell me the best procedure to install ubuntu on my macbook. i have windows installed on it via. bootcamp. I've tried searching it on google but i am reluctant to try out anyone of them.
Thanks in advance.

---

### Post by _mario_ on 2008-12-03
> **naren.bharatwaj said:**
> Can someone tell me the best procedure to install ubuntu on my macbook. i have windows installed on it via. bootcamp. I've tried searching it on google but i am reluctant to try out anyone of them.
Thanks in advance.
the short answer is: shrink your windows partition and create a new one for Ubuntu. the tutorials that use this approach should work.

i assume your partition table looks like this:
[LIST=1]
[*]EFI system partition.
[*]OSX partition
[*]Windows partition.
[/LIST]
depending on the partitioning tool you use (OSX diskutil), the first one might be invisible.

so i'd do:
[LIST=1]
[*]install rEFIt and assure it is working.
[*]defragment the Windows partition.
[*]boot the Ubuntu Live CD.
[*]shrink the Windows partition to gain free space. (use gparted under System > Adminstration.)
[*]follow the installer and select to install to the "largest continuous free space". (manually creating a new partition and selecting it will be fine as well.)
[*]on the last page select 'advanced' and install the GRUB bootloader onto the ubuntu partition, not the MBR. should be /dev/sda4 then. please double check.
[*]reboot and run rEFIt's partitioning tool to re-sync GPT and MBR.
[*]shutdown (not reboot).
[*]boot Ubuntu and have fun. in case Ubuntu doesn't boot, shutdown again.
[/LIST]
of course, you can also create more partitions than Ubuntu's installer does by default (e.g., a separate home partition), but Windows and Ubuntu's boot partition (where the kernel is installed) have to be among the first 4 (including the EFI system partition).

partitions beyond the first four will not be bootable (in legacy BIOS emulation mode), unless you use GRUB EFI, which is more complicated to set up.

ciao,
Mario

---

### Post by naren.bharatwaj on 2008-12-04
Thanks for the help. Just want to know if wubi will create any problems?

Thanks,

Naren

---

### Post by _mario_ on 2008-12-04
> **naren.bharatwaj said:**
> Thanks for the help. Just want to know if wubi will create any problems?
in theory: no. wubi uses a disk file (usually c:\ubuntu\disks\root.disk) instead of a partition and tweaks the windows boot loader to load the linux kernel out of this file. that means you first have to select windows in rEFIt's or the firmware's boot menu. i wouldn't expect any problems, although i've never tried this.

ciao,
Mario

---

### Post by killernat on 2008-12-04
im sry but u sir are confused lol mac windos and linux

---

### Post by cyberdork33 on 2008-12-04
> **killernat said:**
> im sry but u sir are confused lol mac windos and linux

If you have nothing useful to add, please go elsewhere.

---

### Post by acelin on 2008-12-11
> **cyberdork33 said:**
> If you have nothing useful to add, please go elsewhere.

Well I have a useful question...

My Windows partition is really really small... is there a way to increase its size using Mac OS X's partition manager?

---

### Post by beauman on 2008-12-12
> **_mario_ said:**
> the short answer is: shrink your windows partition and create a new one for Ubuntu. the tutorials that use this approach should work.



You can also shrink the Mac HD using diskutil under OS X in a terminal.

To find out what partitions you already have use "diskutil list". On my Mac it looks like: 
```
beaumans-macbook:~ beauman$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                    *149.1 Gi   disk0
   1:                        EFI                     200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD        64.9 Gi    disk0s2
   3:         Microsoft Reserved                     10.0 Gi    disk0s5
   4:                 Linux Swap                     976.6 Mi   disk0s3
   5:       Microsoft Basic Data UNTITLED            73.0 Gi    disk0s4

```

I did lately resize my mac hd:

```

beaumans-macbook:~ beauman$ ls /dev/disk*
/dev/disk0   /dev/disk0s1   /dev/disk0s2   /dev/disk0s3   /dev/disk0s4

beaumans-macbook:~ beauman$ diskutil resizeVolume disk0s2 limits
For device disk0s2 Macintosh HD:
	Current size:	80396419072 bytes
	Minimum size:	32698286080 bytes
	Maximum size:	81286201856 bytes

beaumans-macbook:~ beauman$ diskutil resizeVolume disk0s2 65G
Started resizing on disk disk0s2 Macintosh HD
Verifying
Resizing Volume
Adjusting Partitions
[ + 0%..10%..20%..30%..40%..50%..60%..70%..80%..90%..100% ] 
Finished resizing on disk disk0s2 Macintosh HD
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                    *149.1 Gi   disk0
   1:                        EFI                     200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD        64.9 Gi    disk0s2
   3:                 Linux Swap                     976.6 Mi   disk0s3
   4:       Microsoft Basic Data ibex_on_mac         73.0 Gi    disk0s4



```

Now you can create a swap and an ext3 partition during the installation of Ubuntu.

Remember to sync the partition table with rEFIt at the boot prompt.

see also: [https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation]("https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation")

---

### Post by _mario_ on 2008-12-12
> **acelin said:**
> 
My Windows partition is really really small... is there a way to increase its size using Mac OS X's partition manager?
i don't know whether and how to do this with OSX, but what about using gparted booted off an Ubuntu Live CD?

ciao,
Mario

---

### Post by cyberdork33 on 2008-12-12
> **_mario_ said:**
> i don't know whether and how to do this with OSX, but what about using gparted booted off an Ubuntu Live CD?

ciao,
Mario
I would guess that messing with the windows partition will make windows upset.

---

### Post by acelin on 2008-12-12
I believe that once you edite the partitions with gparted, you cant undo them, as in you cant make it part of the OS X partition again.

---

