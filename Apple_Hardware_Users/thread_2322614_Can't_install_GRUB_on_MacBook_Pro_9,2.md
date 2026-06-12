---
title: "Can't install GRUB on MacBook Pro 9,2"
date: 2016-04-29
forum: Apple Hardware Users
---

### Post by Gorghino on 2016-04-29
**Model**:    MacBookPro9,2
**Boot ROM Version**:    MBP91.00D3.B0C
**SMC Version (system):**    2.2f44
**Hardware UUID**:    4C8F1DF7-6B96-51D6-9307-1A25838C2741

Hi guys,
I'm trying to install Ubuntu 16.04 on my MacBook Pro, without success (Fatal error during grub/Ubuntu setup).
In this moment I've got this OS setting:
- Yosemite 10.10.5 (14F1713) 
- Windows 10 with Bootcamp

```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: DB8AF6B6-61C4-4A2F-A3CD-4052D17BF040

Device          Start        End    Sectors   Size Type
/dev/sda1          40     409639     409600   200M EFI System
/dev/sda2      409640 1651204095 1650794456 787.2G Apple HFS/HFS+
/dev/sda3  1749130600 1750400135    1269536 619.9M Apple boot
/dev/sda4  1750401024 1953523711  203122688  96.9G Microsoft basic data
/dev/sda5  1651204096 1733484543   82280448  39.2G Linux filesystem
/dev/sda6  1733505024 1749129215   15624192   7.5G Linux swap
/dev/sda7  1733484544 1733505023      20480    10M Apple HFS/HFS+

Partition table entries are not in disk order.

```

I was following this guide: [https://glandium.org/blog/?p=2830](https://glandium.org/blog/?p=2830) on my Ubuntu Usb Live.
[LIST]
[*]I installed [COLOR=#000000]hfsprogs_332.25-11_amd64.deb and [/COLOR][COLOR=#000000]icnsutils_0.8.1-1_amd64.deb.
[/COLOR]
[*][COLOR=#000000]I created /dev/sda7 with [/COLOR]```
[COLOR=#000000]sudo mkfs.hfsplus /dev/sda7 -v Ubuntu[/COLOR]
```
[*]I put the entry in /etc/fstab ```
[COLOR=#000000]echo $(blkid -o export -s UUID /dev/sda7) /boot/efi auto defaults 0 0 >> /etc/fstab[/COLOR]
``` but It put "[COLOR=#000000]DEVNAME=/dev/sda7 UUID=cefa376c-1e6d-3c8a-af91-7691902c63b9 /boot/efi auto defaults 0 0" that wasn't correct when I tried to mount it: [/COLOR][COLOR=#000000]```
mount: /etc/fstab: parse error: ignore entry at line 3.
mount: can't find /boot/efi in /etc/fstab

```[/COLOR]
[*][COLOR=#000000]So I removed "[/COLOR][COLOR=#000000]DEVNAME=/dev/sda7" and mount command worked.[/COLOR]
[*][COLOR=#000000]I looked for the block of code with [/COLOR][COLOR=#000000][FONT=monospace]xfat in it, but it doesn't exist; The file isn't actually a script file..[/FONT][/COLOR]
[*][COLOR=#000000][FONT=monospace]Then I tried to install grub:
[/FONT][/COLOR]```
[COLOR=#000000]sudo grub-install 
[/COLOR][COLOR=#000000]Installing for i386-pc platform.
[/COLOR][COLOR=#000000]grub-install: error: install device isn't specified.

[/COLOR]update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
```
[*]I Installed [COLOR=#000000]grub-efi-amd64 and I tried with this command, following "Installing GRUB" section from this guide: [http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/#fixing-efi](http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/#fixing-efi)
```
sudo grub-install --target x86_64-efi --boot-directory=/boot --efi-directory=/boot/efi --bootloader-id="$(lsb_release -ds)"
Installing for x86_64-efi platform.

grub-install: error: failed to get canonical path of `/cow'.
```[/COLOR]
[*]This is grub-install debug log:

```
sudo grub-install --target x86_64-efi --boot-directory=/boot --efi-directory=/boot/efi --bootloader-id="$(lsb_release -ds)" --recheck --debug /dev/sda
Installing for x86_64-efi platform.
grub-install: info: cannot open `/boot/grub/device.map': No such file or directory.
grub-install: info: /dev/sda7 is not present.
grub-install: info: Looking for /dev/sda7.
grub-install: info: /dev/sda is a parent of /dev/sda7.
grub-install: info: /dev/sda7 starts from 1733484544.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 40.
grub-install: info: Partition 1 starts from 409640.
grub-install: info: Partition 2 starts from 1749130600.
grub-install: info: Partition 3 starts from 1750401024.
grub-install: info: Partition 4 starts from 1651204096.
grub-install: info: Partition 5 starts from 1733505024.
grub-install: info: Partition 6 starts from 1733484544.
grub-install: info: /dev/sda7 is present.
grub-install: info: Looking for /dev/sda7.
grub-install: info: /dev/sda is a parent of /dev/sda7.
grub-install: info: /dev/sda7 starts from 1733484544.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 40.
grub-install: info: Partition 1 starts from 409640.
grub-install: info: Partition 2 starts from 1749130600.
grub-install: info: Partition 3 starts from 1750401024.
grub-install: info: Partition 4 starts from 1651204096.
grub-install: info: Partition 5 starts from 1733505024.
grub-install: info: Partition 6 starts from 1733484544.
grub-install: info: /dev/sda7 is present.
grub-install: info: Looking for /dev/sda7.
grub-install: info: /dev/sda is a parent of /dev/sda7.
grub-install: info: /dev/sda7 starts from 1733484544.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 40.
grub-install: info: Partition 1 starts from 409640.
grub-install: info: Partition 2 starts from 1749130600.
grub-install: info: Partition 3 starts from 1750401024.
grub-install: info: Partition 4 starts from 1651204096.
grub-install: info: Partition 5 starts from 1733505024.
grub-install: info: Partition 6 starts from 1733484544.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_camellia.mod' -> `/boot/grub/x86_64-efi/gcry_camellia.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/geli.mod' -> `/boot/grub/x86_64-efi/geli.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbserial_usbdebug.mod' -> `/boot/grub/x86_64-efi/usbserial_usbdebug.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_bsd.mod' -> `/boot/grub/x86_64-efi/part_bsd.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/setpci.mod' -> `/boot/grub/x86_64-efi/setpci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbtable.mod' -> `/boot/grub/x86_64-efi/cbtable.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/fat.mod' -> `/boot/grub/x86_64-efi/fat.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hfspluscomp.mod' -> `/boot/grub/x86_64-efi/hfspluscomp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/linux16.mod' -> `/boot/grub/x86_64-efi/linux16.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_dvh.mod' -> `/boot/grub/x86_64-efi/part_dvh.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsefisystab.mod' -> `/boot/grub/x86_64-efi/lsefisystab.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_blowfish.mod' -> `/boot/grub/x86_64-efi/gcry_blowfish.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xnu_uuid.mod' -> `/boot/grub/x86_64-efi/xnu_uuid.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/offsetio.mod' -> `/boot/grub/x86_64-efi/offsetio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/crypto.mod' -> `/boot/grub/x86_64-efi/crypto.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/read.mod' -> `/boot/grub/x86_64-efi/read.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/relocator.mod' -> `/boot/grub/x86_64-efi/relocator.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/boot.mod' -> `/boot/grub/x86_64-efi/boot.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/password.mod' -> `/boot/grub/x86_64-efi/password.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_sunpc.mod' -> `/boot/grub/x86_64-efi/part_sunpc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lzopio.mod' -> `/boot/grub/x86_64-efi/lzopio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_arcfour.mod' -> `/boot/grub/x86_64-efi/gcry_arcfour.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_apple.mod' -> `/boot/grub/x86_64-efi/part_apple.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/memrw.mod' -> `/boot/grub/x86_64-efi/memrw.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minicmd.mod' -> `/boot/grub/x86_64-efi/minicmd.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cpio_be.mod' -> `/boot/grub/x86_64-efi/cpio_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix3.mod' -> `/boot/grub/x86_64-efi/minix3.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsacpi.mod' -> `/boot/grub/x86_64-efi/lsacpi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cs5536.mod' -> `/boot/grub/x86_64-efi/cs5536.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gfxmenu.mod' -> `/boot/grub/x86_64-efi/gfxmenu.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video_fb.mod' -> `/boot/grub/x86_64-efi/video_fb.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/parttool.mod' -> `/boot/grub/x86_64-efi/parttool.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_rsa.mod' -> `/boot/grub/x86_64-efi/gcry_rsa.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_acorn.mod' -> `/boot/grub/x86_64-efi/part_acorn.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix2.mod' -> `/boot/grub/x86_64-efi/minix2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/signature_test.mod' -> `/boot/grub/x86_64-efi/signature_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/linux.mod' -> `/boot/grub/x86_64-efi/linux.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/blocklist.mod' -> `/boot/grub/x86_64-efi/blocklist.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ehci.mod' -> `/boot/grub/x86_64-efi/ehci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_rijndael.mod' -> `/boot/grub/x86_64-efi/gcry_rijndael.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usb_keyboard.mod' -> `/boot/grub/x86_64-efi/usb_keyboard.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbmemc.mod' -> `/boot/grub/x86_64-efi/cbmemc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gettext.mod' -> `/boot/grub/x86_64-efi/gettext.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_crc.mod' -> `/boot/grub/x86_64-efi/gcry_crc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/loopback.mod' -> `/boot/grub/x86_64-efi/loopback.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/test_blockarg.mod' -> `/boot/grub/x86_64-efi/test_blockarg.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_cast5.mod' -> `/boot/grub/x86_64-efi/gcry_cast5.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/videotest.mod' -> `/boot/grub/x86_64-efi/videotest.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/play.mod' -> `/boot/grub/x86_64-efi/play.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/sleep_test.mod' -> `/boot/grub/x86_64-efi/sleep_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix.mod' -> `/boot/grub/x86_64-efi/minix.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mdraid1x.mod' -> `/boot/grub/x86_64-efi/mdraid1x.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/videoinfo.mod' -> `/boot/grub/x86_64-efi/videoinfo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/multiboot2.mod' -> `/boot/grub/x86_64-efi/multiboot2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gfxterm.mod' -> `/boot/grub/x86_64-efi/gfxterm.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_sha512.mod' -> `/boot/grub/x86_64-efi/gcry_sha512.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/loadbios.mod' -> `/boot/grub/x86_64-efi/loadbios.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hfsplus.mod' -> `/boot/grub/x86_64-efi/hfsplus.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/procfs.mod' -> `/boot/grub/x86_64-efi/procfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_amiga.mod' -> `/boot/grub/x86_64-efi/part_amiga.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/terminal.mod' -> `/boot/grub/x86_64-efi/terminal.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/search.mod' -> `/boot/grub/x86_64-efi/search.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_des.mod' -> `/boot/grub/x86_64-efi/gcry_des.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/dm_nv.mod' -> `/boot/grub/x86_64-efi/dm_nv.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/eval.mod' -> `/boot/grub/x86_64-efi/eval.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video_colors.mod' -> `/boot/grub/x86_64-efi/video_colors.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mdraid09_be.mod' -> `/boot/grub/x86_64-efi/mdraid09_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/sfs.mod' -> `/boot/grub/x86_64-efi/sfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/fshelp.mod' -> `/boot/grub/x86_64-efi/fshelp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix3_be.mod' -> `/boot/grub/x86_64-efi/minix3_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ntfscomp.mod' -> `/boot/grub/x86_64-efi/ntfscomp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsmmap.mod' -> `/boot/grub/x86_64-efi/lsmmap.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/setjmp.mod' -> `/boot/grub/x86_64-efi/setjmp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/png.mod' -> `/boot/grub/x86_64-efi/png.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ohci.mod' -> `/boot/grub/x86_64-efi/ohci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bufio.mod' -> `/boot/grub/x86_64-efi/bufio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/odc.mod' -> `/boot/grub/x86_64-efi/odc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cmdline_cat_test.mod' -> `/boot/grub/x86_64-efi/cmdline_cat_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xnu_uuid_test.mod' -> `/boot/grub/x86_64-efi/xnu_uuid_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/keylayouts.mod' -> `/boot/grub/x86_64-efi/keylayouts.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/time.mod' -> `/boot/grub/x86_64-efi/time.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/macho.mod' -> `/boot/grub/x86_64-efi/macho.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/pbkdf2_test.mod' -> `/boot/grub/x86_64-efi/pbkdf2_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbtest.mod' -> `/boot/grub/x86_64-efi/usbtest.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/help.mod' -> `/boot/grub/x86_64-efi/help.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/morse.mod' -> `/boot/grub/x86_64-efi/morse.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/setjmp_test.mod' -> `/boot/grub/x86_64-efi/setjmp_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/scsi.mod' -> `/boot/grub/x86_64-efi/scsi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/linuxefi.mod' -> `/boot/grub/x86_64-efi/linuxefi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/all_video.mod' -> `/boot/grub/x86_64-efi/all_video.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/regexp.mod' -> `/boot/grub/x86_64-efi/regexp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsefimmap.mod' -> `/boot/grub/x86_64-efi/lsefimmap.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/extcmd.mod' -> `/boot/grub/x86_64-efi/extcmd.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hexdump.mod' -> `/boot/grub/x86_64-efi/hexdump.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/disk.mod' -> `/boot/grub/x86_64-efi/disk.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/syslinuxcfg.mod' -> `/boot/grub/x86_64-efi/syslinuxcfg.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hello.mod' -> `/boot/grub/x86_64-efi/hello.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/search_label.mod' -> `/boot/grub/x86_64-efi/search_label.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/btrfs.mod' -> `/boot/grub/x86_64-efi/btrfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/jpeg.mod' -> `/boot/grub/x86_64-efi/jpeg.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cpuid.mod' -> `/boot/grub/x86_64-efi/cpuid.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/priority_queue.mod' -> `/boot/grub/x86_64-efi/priority_queue.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/reiserfs.mod' -> `/boot/grub/x86_64-efi/reiserfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/serial.mod' -> `/boot/grub/x86_64-efi/serial.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/spkmodem.mod' -> `/boot/grub/x86_64-efi/spkmodem.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/keystatus.mod' -> `/boot/grub/x86_64-efi/keystatus.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lsefi.mod' -> `/boot/grub/x86_64-efi/lsefi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bitmap.mod' -> `/boot/grub/x86_64-efi/bitmap.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cryptodisk.mod' -> `/boot/grub/x86_64-efi/cryptodisk.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lssal.mod' -> `/boot/grub/x86_64-efi/lssal.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/nativedisk.mod' -> `/boot/grub/x86_64-efi/nativedisk.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/terminfo.mod' -> `/boot/grub/x86_64-efi/terminfo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_twofish.mod' -> `/boot/grub/x86_64-efi/gcry_twofish.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_md4.mod' -> `/boot/grub/x86_64-efi/gcry_md4.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video_bochs.mod' -> `/boot/grub/x86_64-efi/video_bochs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_sha256.mod' -> `/boot/grub/x86_64-efi/gcry_sha256.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ufs2.mod' -> `/boot/grub/x86_64-efi/ufs2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bfs.mod' -> `/boot/grub/x86_64-efi/bfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/videotest_checksum.mod' -> `/boot/grub/x86_64-efi/videotest_checksum.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/afs.mod' -> `/boot/grub/x86_64-efi/afs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/pcidump.mod' -> `/boot/grub/x86_64-efi/pcidump.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_tiger.mod' -> `/boot/grub/x86_64-efi/gcry_tiger.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xfs.mod' -> `/boot/grub/x86_64-efi/xfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_dfly.mod' -> `/boot/grub/x86_64-efi/part_dfly.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/echo.mod' -> `/boot/grub/x86_64-efi/echo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_md5.mod' -> `/boot/grub/x86_64-efi/gcry_md5.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/multiboot.mod' -> `/boot/grub/x86_64-efi/multiboot.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/romfs.mod' -> `/boot/grub/x86_64-efi/romfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xzio.mod' -> `/boot/grub/x86_64-efi/xzio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ufs1_be.mod' -> `/boot/grub/x86_64-efi/ufs1_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/verify.mod' -> `/boot/grub/x86_64-efi/verify.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/memdisk.mod' -> `/boot/grub/x86_64-efi/memdisk.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lspci.mod' -> `/boot/grub/x86_64-efi/lspci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/iso9660.mod' -> `/boot/grub/x86_64-efi/iso9660.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/chain.mod' -> `/boot/grub/x86_64-efi/chain.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/zfscrypt.mod' -> `/boot/grub/x86_64-efi/zfscrypt.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/acpi.mod' -> `/boot/grub/x86_64-efi/acpi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/newc.mod' -> `/boot/grub/x86_64-efi/newc.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/jfs.mod' -> `/boot/grub/x86_64-efi/jfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/nilfs2.mod' -> `/boot/grub/x86_64-efi/nilfs2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_idea.mod' -> `/boot/grub/x86_64-efi/gcry_idea.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cat.mod' -> `/boot/grub/x86_64-efi/cat.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/pata.mod' -> `/boot/grub/x86_64-efi/pata.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_rfc2268.mod' -> `/boot/grub/x86_64-efi/gcry_rfc2268.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/exfat.mod' -> `/boot/grub/x86_64-efi/exfat.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_msdos.mod' -> `/boot/grub/x86_64-efi/part_msdos.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbls.mod' -> `/boot/grub/x86_64-efi/cbls.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/zfs.mod' -> `/boot/grub/x86_64-efi/zfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usb.mod' -> `/boot/grub/x86_64-efi/usb.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/squash4.mod' -> `/boot/grub/x86_64-efi/squash4.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbms.mod' -> `/boot/grub/x86_64-efi/usbms.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bsd.mod' -> `/boot/grub/x86_64-efi/bsd.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/raid5rec.mod' -> `/boot/grub/x86_64-efi/raid5rec.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_plan.mod' -> `/boot/grub/x86_64-efi/part_plan.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/normal.mod' -> `/boot/grub/x86_64-efi/normal.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbtime.mod' -> `/boot/grub/x86_64-efi/cbtime.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/udf.mod' -> `/boot/grub/x86_64-efi/udf.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/net.mod' -> `/boot/grub/x86_64-efi/net.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hfs.mod' -> `/boot/grub/x86_64-efi/hfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/testload.mod' -> `/boot/grub/x86_64-efi/testload.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/adler32.mod' -> `/boot/grub/x86_64-efi/adler32.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/configfile.mod' -> `/boot/grub/x86_64-efi/configfile.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/raid6rec.mod' -> `/boot/grub/x86_64-efi/raid6rec.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/msdospart.mod' -> `/boot/grub/x86_64-efi/msdospart.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/date.mod' -> `/boot/grub/x86_64-efi/date.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/http.mod' -> `/boot/grub/x86_64-efi/http.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efi_gop.mod' -> `/boot/grub/x86_64-efi/efi_gop.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_whirlpool.mod' -> `/boot/grub/x86_64-efi/gcry_whirlpool.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/diskfilter.mod' -> `/boot/grub/x86_64-efi/diskfilter.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cbfs.mod' -> `/boot/grub/x86_64-efi/cbfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/tftp.mod' -> `/boot/grub/x86_64-efi/tftp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ext2.mod' -> `/boot/grub/x86_64-efi/ext2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/uhci.mod' -> `/boot/grub/x86_64-efi/uhci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video.mod' -> `/boot/grub/x86_64-efi/video.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/pbkdf2.mod' -> `/boot/grub/x86_64-efi/pbkdf2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/crc64.mod' -> `/boot/grub/x86_64-efi/crc64.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gptsync.mod' -> `/boot/grub/x86_64-efi/gptsync.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix_be.mod' -> `/boot/grub/x86_64-efi/minix_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/datehook.mod' -> `/boot/grub/x86_64-efi/datehook.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hdparm.mod' -> `/boot/grub/x86_64-efi/hdparm.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/luks.mod' -> `/boot/grub/x86_64-efi/luks.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/macbless.mod' -> `/boot/grub/x86_64-efi/macbless.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/tga.mod' -> `/boot/grub/x86_64-efi/tga.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/file.mod' -> `/boot/grub/x86_64-efi/file.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/hashsum.mod' -> `/boot/grub/x86_64-efi/hashsum.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/datetime.mod' -> `/boot/grub/x86_64-efi/datetime.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video_cirrus.mod' -> `/boot/grub/x86_64-efi/video_cirrus.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efi_uga.mod' -> `/boot/grub/x86_64-efi/efi_uga.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/testspeed.mod' -> `/boot/grub/x86_64-efi/testspeed.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/affs.mod' -> `/boot/grub/x86_64-efi/affs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cpio.mod' -> `/boot/grub/x86_64-efi/cpio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/at_keyboard.mod' -> `/boot/grub/x86_64-efi/at_keyboard.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/elf.mod' -> `/boot/grub/x86_64-efi/elf.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/fixvideo.mod' -> `/boot/grub/x86_64-efi/fixvideo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/tr.mod' -> `/boot/grub/x86_64-efi/tr.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbserial_pl2303.mod' -> `/boot/grub/x86_64-efi/usbserial_pl2303.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/search_fs_file.mod' -> `/boot/grub/x86_64-efi/search_fs_file.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/sleep.mod' -> `/boot/grub/x86_64-efi/sleep.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_sha1.mod' -> `/boot/grub/x86_64-efi/gcry_sha1.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/trig.mod' -> `/boot/grub/x86_64-efi/trig.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ata.mod' -> `/boot/grub/x86_64-efi/ata.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/progress.mod' -> `/boot/grub/x86_64-efi/progress.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ls.mod' -> `/boot/grub/x86_64-efi/ls.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efinet.mod' -> `/boot/grub/x86_64-efi/efinet.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/cmp.mod' -> `/boot/grub/x86_64-efi/cmp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/functional_test.mod' -> `/boot/grub/x86_64-efi/functional_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbserial_ftdi.mod' -> `/boot/grub/x86_64-efi/usbserial_ftdi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mmap.mod' -> `/boot/grub/x86_64-efi/mmap.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/reboot.mod' -> `/boot/grub/x86_64-efi/reboot.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_dsa.mod' -> `/boot/grub/x86_64-efi/gcry_dsa.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/password_pbkdf2.mod' -> `/boot/grub/x86_64-efi/password_pbkdf2.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/probe.mod' -> `/boot/grub/x86_64-efi/probe.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/iorw.mod' -> `/boot/grub/x86_64-efi/iorw.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/usbserial_common.mod' -> `/boot/grub/x86_64-efi/usbserial_common.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_sun.mod' -> `/boot/grub/x86_64-efi/part_sun.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/legacy_password_test.mod' -> `/boot/grub/x86_64-efi/legacy_password_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/div_test.mod' -> `/boot/grub/x86_64-efi/div_test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/aout.mod' -> `/boot/grub/x86_64-efi/aout.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/zfsinfo.mod' -> `/boot/grub/x86_64-efi/zfsinfo.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/lvm.mod' -> `/boot/grub/x86_64-efi/lvm.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/xnu.mod' -> `/boot/grub/x86_64-efi/xnu.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/archelp.mod' -> `/boot/grub/x86_64-efi/archelp.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gfxterm_background.mod' -> `/boot/grub/x86_64-efi/gfxterm_background.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ldm.mod' -> `/boot/grub/x86_64-efi/ldm.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efifwsetup.mod' -> `/boot/grub/x86_64-efi/efifwsetup.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mdraid09.mod' -> `/boot/grub/x86_64-efi/mdraid09.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_seed.mod' -> `/boot/grub/x86_64-efi/gcry_seed.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/legacycfg.mod' -> `/boot/grub/x86_64-efi/legacycfg.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/test.mod' -> `/boot/grub/x86_64-efi/test.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gzio.mod' -> `/boot/grub/x86_64-efi/gzio.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/search_fs_uuid.mod' -> `/boot/grub/x86_64-efi/search_fs_uuid.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_rmd160.mod' -> `/boot/grub/x86_64-efi/gcry_rmd160.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gfxterm_menu.mod' -> `/boot/grub/x86_64-efi/gfxterm_menu.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/part_gpt.mod' -> `/boot/grub/x86_64-efi/part_gpt.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/bitmap_scale.mod' -> `/boot/grub/x86_64-efi/bitmap_scale.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/backtrace.mod' -> `/boot/grub/x86_64-efi/backtrace.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/loadenv.mod' -> `/boot/grub/x86_64-efi/loadenv.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ufs1.mod' -> `/boot/grub/x86_64-efi/ufs1.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/minix2_be.mod' -> `/boot/grub/x86_64-efi/minix2_be.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/font.mod' -> `/boot/grub/x86_64-efi/font.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/true.mod' -> `/boot/grub/x86_64-efi/true.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/tar.mod' -> `/boot/grub/x86_64-efi/tar.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/gcry_serpent.mod' -> `/boot/grub/x86_64-efi/gcry_serpent.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ntfs.mod' -> `/boot/grub/x86_64-efi/ntfs.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/appleldr.mod' -> `/boot/grub/x86_64-efi/appleldr.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/ahci.mod' -> `/boot/grub/x86_64-efi/ahci.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/exfctest.mod' -> `/boot/grub/x86_64-efi/exfctest.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/halt.mod' -> `/boot/grub/x86_64-efi/halt.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/mpi.mod' -> `/boot/grub/x86_64-efi/mpi.mod'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efiemu32.o' -> `/boot/grub/x86_64-efi/efiemu32.o'.
grub-install: info: cannot open `/usr/lib/grub/x86_64-efi/efiemu32.o': No such file or directory.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/efiemu64.o' -> `/boot/grub/x86_64-efi/efiemu64.o'.
grub-install: info: cannot open `/usr/lib/grub/x86_64-efi/efiemu64.o': No such file or directory.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/moddep.lst' -> `/boot/grub/x86_64-efi/moddep.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/command.lst' -> `/boot/grub/x86_64-efi/command.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/fs.lst' -> `/boot/grub/x86_64-efi/fs.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/partmap.lst' -> `/boot/grub/x86_64-efi/partmap.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/parttool.lst' -> `/boot/grub/x86_64-efi/parttool.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/video.lst' -> `/boot/grub/x86_64-efi/video.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/crypto.lst' -> `/boot/grub/x86_64-efi/crypto.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/terminal.lst' -> `/boot/grub/x86_64-efi/terminal.lst'.
grub-install: info: copying `/usr/lib/grub/x86_64-efi/modinfo.sh' -> `/boot/grub/x86_64-efi/modinfo.sh'.
grub-install: info: copying `/usr/share/locale/aa/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/aa.mo'.
grub-install: info: cannot open `/usr/share/locale/aa/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ace/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ace.mo'.
grub-install: info: cannot open `/usr/share/locale/ace/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/af/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/af.mo'.
grub-install: info: cannot open `/usr/share/locale/af/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/am/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/am.mo'.
grub-install: info: cannot open `/usr/share/locale/am/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/an/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/an.mo'.
grub-install: info: cannot open `/usr/share/locale/an/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ar/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ar.mo'.
grub-install: info: cannot open `/usr/share/locale/ar/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ary/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ary.mo'.
grub-install: info: cannot open `/usr/share/locale/ary/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/as/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/as.mo'.
grub-install: info: cannot open `/usr/share/locale/as/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ast/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ast.mo'.
grub-install: info: cannot open `/usr/share/locale/ast/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/az/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/az.mo'.
grub-install: info: cannot open `/usr/share/locale/az/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/be/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/be.mo'.
grub-install: info: cannot open `/usr/share/locale/be/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/be@latin/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/be@latin.mo'.
grub-install: info: cannot open `/usr/share/locale/be@latin/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bem/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bem.mo'.
grub-install: info: cannot open `/usr/share/locale/bem/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bg/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bg.mo'.
grub-install: info: cannot open `/usr/share/locale/bg/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bn.mo'.
grub-install: info: cannot open `/usr/share/locale/bn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bn_IN/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bn_IN.mo'.
grub-install: info: cannot open `/usr/share/locale/bn_IN/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bo.mo'.
grub-install: info: cannot open `/usr/share/locale/bo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/br/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/br.mo'.
grub-install: info: cannot open `/usr/share/locale/br/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/bs/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/bs.mo'.
grub-install: info: cannot open `/usr/share/locale/bs/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/byn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/byn.mo'.
grub-install: info: cannot open `/usr/share/locale/byn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ca/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ca.mo'.
grub-install: info: cannot open `/usr/share/locale/ca/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ca@valencia/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ca@valencia.mo'.
grub-install: info: cannot open `/usr/share/locale/ca@valencia/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ce/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ce.mo'.
grub-install: info: cannot open `/usr/share/locale/ce/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/chr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/chr.mo'.
grub-install: info: cannot open `/usr/share/locale/chr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ckb/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ckb.mo'.
grub-install: info: cannot open `/usr/share/locale/ckb/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/crh/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/crh.mo'.
grub-install: info: cannot open `/usr/share/locale/crh/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/cs/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/cs.mo'.
grub-install: info: cannot open `/usr/share/locale/cs/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/csb/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/csb.mo'.
grub-install: info: cannot open `/usr/share/locale/csb/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/cv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/cv.mo'.
grub-install: info: cannot open `/usr/share/locale/cv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/cy/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/cy.mo'.
grub-install: info: cannot open `/usr/share/locale/cy/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/da/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/da.mo'.
grub-install: info: cannot open `/usr/share/locale/da/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/de/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/de.mo'.
grub-install: info: cannot open `/usr/share/locale/de/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/de_DE/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/de_DE.mo'.
grub-install: info: cannot open `/usr/share/locale/de_DE/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/dv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/dv.mo'.
grub-install: info: cannot open `/usr/share/locale/dv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/dz/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/dz.mo'.
grub-install: info: cannot open `/usr/share/locale/dz/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/el/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/el.mo'.
grub-install: info: cannot open `/usr/share/locale/el/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en.mo'.
grub-install: info: cannot open `/usr/share/locale/en/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en_AU/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_AU.mo'.
grub-install: info: cannot open `/usr/share/locale/en_AU/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en_CA/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_CA.mo'.
grub-install: info: cannot open `/usr/share/locale/en_CA/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/en_GB/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_GB.mo'.
grub-install: info: cannot open `/usr/share/locale/en_GB/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/eo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/eo.mo'.
grub-install: info: cannot open `/usr/share/locale/eo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/es/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/es.mo'.
grub-install: info: cannot open `/usr/share/locale/es/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/et/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/et.mo'.
grub-install: info: cannot open `/usr/share/locale/et/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/eu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/eu.mo'.
grub-install: info: cannot open `/usr/share/locale/eu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fa/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fa.mo'.
grub-install: info: cannot open `/usr/share/locale/fa/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fa_AF/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fa_AF.mo'.
grub-install: info: cannot open `/usr/share/locale/fa_AF/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fi/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fi.mo'.
grub-install: info: cannot open `/usr/share/locale/fi/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fil/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fil.mo'.
grub-install: info: cannot open `/usr/share/locale/fil/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fo.mo'.
grub-install: info: cannot open `/usr/share/locale/fo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fr.mo'.
grub-install: info: cannot open `/usr/share/locale/fr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fr_CA/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fr_CA.mo'.
grub-install: info: cannot open `/usr/share/locale/fr_CA/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/frp/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/frp.mo'.
grub-install: info: cannot open `/usr/share/locale/frp/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fur/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fur.mo'.
grub-install: info: cannot open `/usr/share/locale/fur/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/fy/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fy.mo'.
grub-install: info: cannot open `/usr/share/locale/fy/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ga/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ga.mo'.
grub-install: info: cannot open `/usr/share/locale/ga/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gd/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gd.mo'.
grub-install: info: cannot open `/usr/share/locale/gd/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gez/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gez.mo'.
grub-install: info: cannot open `/usr/share/locale/gez/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gl.mo'.
grub-install: info: cannot open `/usr/share/locale/gl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gu.mo'.
grub-install: info: cannot open `/usr/share/locale/gu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/gv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/gv.mo'.
grub-install: info: cannot open `/usr/share/locale/gv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/haw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/haw.mo'.
grub-install: info: cannot open `/usr/share/locale/haw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/he/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/he.mo'.
grub-install: info: cannot open `/usr/share/locale/he/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/hi/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/hi.mo'.
grub-install: info: cannot open `/usr/share/locale/hi/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/hr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/hr.mo'.
grub-install: info: cannot open `/usr/share/locale/hr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ht/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ht.mo'.
grub-install: info: cannot open `/usr/share/locale/ht/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/hu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/hu.mo'.
grub-install: info: cannot open `/usr/share/locale/hu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/hy/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/hy.mo'.
grub-install: info: cannot open `/usr/share/locale/hy/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ia/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ia.mo'.
grub-install: info: cannot open `/usr/share/locale/ia/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/id/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/id.mo'.
grub-install: info: cannot open `/usr/share/locale/id/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/is/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/is.mo'.
grub-install: info: cannot open `/usr/share/locale/is/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/it/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/it.mo'.
grub-install: info: cannot open `/usr/share/locale/it/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ja/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ja.mo'.
grub-install: info: cannot open `/usr/share/locale/ja/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/jv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/jv.mo'.
grub-install: info: cannot open `/usr/share/locale/jv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ka/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ka.mo'.
grub-install: info: cannot open `/usr/share/locale/ka/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kk.mo'.
grub-install: info: cannot open `/usr/share/locale/kk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kl.mo'.
grub-install: info: cannot open `/usr/share/locale/kl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/km/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/km.mo'.
grub-install: info: cannot open `/usr/share/locale/km/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kn.mo'.
grub-install: info: cannot open `/usr/share/locale/kn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ko/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ko.mo'.
grub-install: info: cannot open `/usr/share/locale/ko/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kok/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kok.mo'.
grub-install: info: cannot open `/usr/share/locale/kok/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ku/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ku.mo'.
grub-install: info: cannot open `/usr/share/locale/ku/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/kw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/kw.mo'.
grub-install: info: cannot open `/usr/share/locale/kw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ky/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ky.mo'.
grub-install: info: cannot open `/usr/share/locale/ky/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/lb/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/lb.mo'.
grub-install: info: cannot open `/usr/share/locale/lb/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ln/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ln.mo'.
grub-install: info: cannot open `/usr/share/locale/ln/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/lo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/lo.mo'.
grub-install: info: cannot open `/usr/share/locale/lo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/locale.alias/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/locale.alias.mo'.
grub-install: info: cannot open `/usr/share/locale/locale.alias/LC_MESSAGES/grub.mo': Not a directory.
grub-install: info: copying `/usr/share/locale/lt/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/lt.mo'.
grub-install: info: cannot open `/usr/share/locale/lt/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/lv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/lv.mo'.
grub-install: info: cannot open `/usr/share/locale/lv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mg/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mg.mo'.
grub-install: info: cannot open `/usr/share/locale/mg/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mhr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mhr.mo'.
grub-install: info: cannot open `/usr/share/locale/mhr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mi/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mi.mo'.
grub-install: info: cannot open `/usr/share/locale/mi/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mk.mo'.
grub-install: info: cannot open `/usr/share/locale/mk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ml/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ml.mo'.
grub-install: info: cannot open `/usr/share/locale/ml/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mn.mo'.
grub-install: info: cannot open `/usr/share/locale/mn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mr.mo'.
grub-install: info: cannot open `/usr/share/locale/mr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ms/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ms.mo'.
grub-install: info: cannot open `/usr/share/locale/ms/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/mt/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/mt.mo'.
grub-install: info: cannot open `/usr/share/locale/mt/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/my/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/my.mo'.
grub-install: info: cannot open `/usr/share/locale/my/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nb/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nb.mo'.
grub-install: info: cannot open `/usr/share/locale/nb/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nds/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nds.mo'.
grub-install: info: cannot open `/usr/share/locale/nds/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ne/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ne.mo'.
grub-install: info: cannot open `/usr/share/locale/ne/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nl.mo'.
grub-install: info: cannot open `/usr/share/locale/nl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nn.mo'.
grub-install: info: cannot open `/usr/share/locale/nn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/nso/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/nso.mo'.
grub-install: info: cannot open `/usr/share/locale/nso/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/oc/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/oc.mo'.
grub-install: info: cannot open `/usr/share/locale/oc/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/om/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/om.mo'.
grub-install: info: cannot open `/usr/share/locale/om/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/or/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/or.mo'.
grub-install: info: cannot open `/usr/share/locale/or/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/os/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/os.mo'.
grub-install: info: cannot open `/usr/share/locale/os/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pa/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pa.mo'.
grub-install: info: cannot open `/usr/share/locale/pa/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pam/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pam.mo'.
grub-install: info: cannot open `/usr/share/locale/pam/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pl.mo'.
grub-install: info: cannot open `/usr/share/locale/pl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ps/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ps.mo'.
grub-install: info: cannot open `/usr/share/locale/ps/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pt/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pt.mo'.
grub-install: info: cannot open `/usr/share/locale/pt/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pt_BR/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pt_BR.mo'.
grub-install: info: cannot open `/usr/share/locale/pt_BR/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/pt_PT/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pt_PT.mo'.
grub-install: info: cannot open `/usr/share/locale/pt_PT/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/qu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/qu.mo'.
grub-install: info: cannot open `/usr/share/locale/qu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ro/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ro.mo'.
grub-install: info: cannot open `/usr/share/locale/ro/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ru/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ru.mo'.
grub-install: info: cannot open `/usr/share/locale/ru/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/rw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/rw.mo'.
grub-install: info: cannot open `/usr/share/locale/rw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sa/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sa.mo'.
grub-install: info: cannot open `/usr/share/locale/sa/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sc/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sc.mo'.
grub-install: info: cannot open `/usr/share/locale/sc/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sco/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sco.mo'.
grub-install: info: cannot open `/usr/share/locale/sco/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sd/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sd.mo'.
grub-install: info: cannot open `/usr/share/locale/sd/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/se/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/se.mo'.
grub-install: info: cannot open `/usr/share/locale/se/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/shn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/shn.mo'.
grub-install: info: cannot open `/usr/share/locale/shn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/si/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/si.mo'.
grub-install: info: cannot open `/usr/share/locale/si/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sk.mo'.
grub-install: info: cannot open `/usr/share/locale/sk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sl.mo'.
grub-install: info: cannot open `/usr/share/locale/sl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sml/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sml.mo'.
grub-install: info: cannot open `/usr/share/locale/sml/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sn.mo'.
grub-install: info: cannot open `/usr/share/locale/sn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/so/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/so.mo'.
grub-install: info: cannot open `/usr/share/locale/so/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sq/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sq.mo'.
grub-install: info: cannot open `/usr/share/locale/sq/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sr.mo'.
grub-install: info: cannot open `/usr/share/locale/sr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sr@Latn/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sr@Latn.mo'.
grub-install: info: cannot open `/usr/share/locale/sr@Latn/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sr@latin/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sr@latin.mo'.
grub-install: info: cannot open `/usr/share/locale/sr@latin/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/st/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/st.mo'.
grub-install: info: cannot open `/usr/share/locale/st/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sv.mo'.
grub-install: info: cannot open `/usr/share/locale/sv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/sw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/sw.mo'.
grub-install: info: cannot open `/usr/share/locale/sw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/szl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/szl.mo'.
grub-install: info: cannot open `/usr/share/locale/szl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ta/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ta.mo'.
grub-install: info: cannot open `/usr/share/locale/ta/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ta_LK/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ta_LK.mo'.
grub-install: info: cannot open `/usr/share/locale/ta_LK/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/te/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/te.mo'.
grub-install: info: cannot open `/usr/share/locale/te/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tg/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tg.mo'.
grub-install: info: cannot open `/usr/share/locale/tg/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/th/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/th.mo'.
grub-install: info: cannot open `/usr/share/locale/th/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ti/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ti.mo'.
grub-install: info: cannot open `/usr/share/locale/ti/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tig/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tig.mo'.
grub-install: info: cannot open `/usr/share/locale/tig/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tk.mo'.
grub-install: info: cannot open `/usr/share/locale/tk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tl/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tl.mo'.
grub-install: info: cannot open `/usr/share/locale/tl/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tr.mo'.
grub-install: info: cannot open `/usr/share/locale/tr/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/trv/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/trv.mo'.
grub-install: info: cannot open `/usr/share/locale/trv/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tt/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tt.mo'.
grub-install: info: cannot open `/usr/share/locale/tt/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/tt@iqtelif/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/tt@iqtelif.mo'.
grub-install: info: cannot open `/usr/share/locale/tt@iqtelif/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ug/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ug.mo'.
grub-install: info: cannot open `/usr/share/locale/ug/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/uk/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/uk.mo'.
grub-install: info: cannot open `/usr/share/locale/uk/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ur/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ur.mo'.
grub-install: info: cannot open `/usr/share/locale/ur/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/uz/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/uz.mo'.
grub-install: info: cannot open `/usr/share/locale/uz/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/ve/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ve.mo'.
grub-install: info: cannot open `/usr/share/locale/ve/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/vec/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/vec.mo'.
grub-install: info: cannot open `/usr/share/locale/vec/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/vi/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/vi.mo'.
grub-install: info: cannot open `/usr/share/locale/vi/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/wa/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/wa.mo'.
grub-install: info: cannot open `/usr/share/locale/wa/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/wae/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/wae.mo'.
grub-install: info: cannot open `/usr/share/locale/wae/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/wal/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/wal.mo'.
grub-install: info: cannot open `/usr/share/locale/wal/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/wo/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/wo.mo'.
grub-install: info: cannot open `/usr/share/locale/wo/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/xh/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/xh.mo'.
grub-install: info: cannot open `/usr/share/locale/xh/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/zh_CN/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zh_CN.mo'.
grub-install: info: cannot open `/usr/share/locale/zh_CN/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/zh_HK/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zh_HK.mo'.
grub-install: info: cannot open `/usr/share/locale/zh_HK/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/zh_TW/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zh_TW.mo'.
grub-install: info: cannot open `/usr/share/locale/zh_TW/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale/zu/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zu.mo'.
grub-install: info: cannot open `/usr/share/locale/zu/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/de/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/de.mo'.
grub-install: info: copying `/usr/share/locale-langpack/en/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en@boldquot/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en@boldquot.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en@boldquot/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en@quot/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en@quot.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en@quot/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en@shaw/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en@shaw.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en@shaw/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en_AU/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_AU.mo'.
grub-install: info: copying `/usr/share/locale-langpack/en_CA/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_CA.mo'.
grub-install: info: copying `/usr/share/locale-langpack/en_GB/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_GB.mo'.
grub-install: info: copying `/usr/share/locale-langpack/en_US/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_US.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en_US/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/en_US@piglatin/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/en_US@piglatin.mo'.
grub-install: info: cannot open `/usr/share/locale-langpack/en_US@piglatin/LC_MESSAGES/grub.mo': No such file or directory.
grub-install: info: copying `/usr/share/locale-langpack/es/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/es.mo'.
grub-install: info: copying `/usr/share/locale-langpack/fr/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/fr.mo'.
grub-install: info: copying `/usr/share/locale-langpack/it/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/it.mo'.
grub-install: info: copying `/usr/share/locale-langpack/pt/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pt.mo'.
grub-install: info: copying `/usr/share/locale-langpack/pt_BR/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/pt_BR.mo'.
grub-install: info: copying `/usr/share/locale-langpack/ru/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/ru.mo'.
grub-install: info: copying `/usr/share/locale-langpack/zh_CN/LC_MESSAGES/grub.mo' -> `/boot/grub/locale/zh_CN.mo'.
grub-install: info: copying `/usr/share/grub/unicode.pf2' -> `/boot/grub/fonts/unicode.pf2'.
grub-install: error: failed to get canonical path of `/cow'.
```
[/LIST]

Could someone help me? Have you got a setup procedure without wiping all my partitions?
If you need more info, ask me :)

---

