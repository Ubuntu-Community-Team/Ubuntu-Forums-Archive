---
title: "GRUB-PC booting Apples"
date: 2009-10-07
forum: Apple Hardware Users
---

### Post by pxwpxw on 2009-10-07
20091007

Thread for grub-pc (grub2) issues for Apple Mac.

This is meant for general discussion, ways to use grub-pc, which is installed by default now with Karmic beta, but can also be installed back to Intrepid.
The current version is grub1.97 latest is beta4.

General Grub2 basics -

Grub 2 (1.97~beta3-1ubuntu8 as of Karmic Beta)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

GRUB 2 Introduction
[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

Following post is about one application, booting from an ubuntu live desktop iso on HD.

---

### Post by pxwpxw on 2009-10-07
grub2 grub-pc /boot/grub/grub.cfg menuentry for loop mount iso 
(The grub loopback command was also available in grub0.97, might work, but would use the old menu.lst format)

```

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries

menuentry "slax iso desktop" {
	search --set -f /slax-6.1.2.iso
	loopback iso /slax-6.1.2.iso
	linux (iso)/boot/vmlinuz from=/slax-6.1.2.iso ramdisk_size=6666 root=/dev/ram0 rw changes=/slax/
	initrd (iso)/boot/initrd.gz
}

menuentry "ubuntu-9.04-desktop-amd64.iso " {
 search --set -f /ubuntu-9.04-desktop-amd64.iso
 loopback loop /ubuntu-9.04-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-9.04-desktop-amd64.iso vga=773 persistent
 initrd (loop)/casper/initrd.gz
}
# other options for linux - acpi=off noapm noapic nolapic
menuentry "ubuntu-9.10-beta-desktop-amd64.iso " {
 search --set -f /ubuntu-9.10-beta-desktop-amd64.iso
 loopback loop /ubuntu-9.10-beta-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-9.10-beta-desktop-amd64.iso vga=773 persistent
 initrd (loop)/casper/initrd.lz
}

### END /etc/grub.d/40_custom ###

```

---

### Post by pxwpxw on 2009-10-07
Booting from live desktop iso's on HD, grub-pc was installed to dev/sda MBR from a Debian501 amd64 (lenny) on dev/sda4, which had grub1.96 early version.

Three live desktop iso's on (ext3) /dev/sda4 root / 
slax  slax-6.1.2.iso			(2.6.28 )
jaunty ubuntu-9.04-desktop-amd64.iso        ( 2.6.28 )
karmic  ubuntu-9.10-beta-desktop-amd64.iso   ( 2.6.31-11-generic #36-Ubuntu )

The ubuntu casper-rw peristence partition (ext3) on /dev/sda7

As seen by parted -
```

root@ubuntu:/home/ubuntu# parted /dev/sda p free
Model: ATA WDC WD3200AAJS-4 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system      Name                  Flags
        17.4kB  20.5kB  3072B   Free Space
 1      20.5kB  210MB   210MB   fat32            EFI System Partition  boot
 2      210MB   44.2GB  44.0GB  hfs+             Untitled
        44.2GB  44.3GB  134MB   Free Space
 3      44.3GB  54.9GB  10.6GB  hfs+             Apple_HFS_Untitled_2
        54.9GB  55.0GB  134MB   Free Space
 4      55.0GB  95.0GB  40.0GB  ext3             root4
 5      95.0GB  98.1GB  3083MB  linux-swap(new)
 6      98.1GB  138GB   40.0GB  ext3             root2
        138GB   138GB   848kB   Free Space
 7      138GB   140GB   2097MB  ext3
        140GB   320GB   180GB   Free Space


---------------------------------------

```


Persistence

For a live usb stick, a 1GB casper-rw can be put on the same partition as the iso 
```

# dd if=/dev/zero of=casper-rw bs=1M count=1K
# mkfs.ext3 -F casper-rw

```

But for the HD iso loop, a casper-rw persistent file on the same partition as the iso and a Debian installation did not seem to work. Perhaps it would if the iso was on a clean partition. So gparted was used to create a new 2GB ext3 partition on HD named casper-rw. That works for karmic and jaunty, in fact they can both use it but with some messy results initially when changing over, probably disastrous later on.

There is no problem with the default X driver when booted by grub-pc (bios boot), so no need to make scripts to change xorg driver.

---

