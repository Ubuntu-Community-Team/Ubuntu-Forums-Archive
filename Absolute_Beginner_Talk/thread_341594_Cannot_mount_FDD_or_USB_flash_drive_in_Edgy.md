---
title: "Cannot mount FDD or USB flash drive in Edgy"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Charlie Wilkes on 2007-01-18
There is another current thread about this, but it involves a different hardware configuration (no cd-rom drive whereas my system has 2 cd-rom drives).

My floppy drive is a generic internal FDD and my flash drive is a PNY attache 512mb.

One of the participants in the other thread suggested some command strings to get a diagnostic readout, so I typed them in to my system and got the information below.

Can anyone suggest how I might go about fixing this problem?  Thanks!

Charlie

===========================================

charlie@charlie-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Can anyone suggest how I might go about fixing this problem?  Thanks!

Charlie
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4776    38363188+  83  Linux
/dev/hda2            4777        4982     1654695    5  Extended
/dev/hda5            4777        4982     1654663+  82  Linux swap / Solaris
charlie@charlie-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              37G  2.3G   32G   7% /
varrun                316M   80K  316M   1% /var/run
varlock               316M     0  316M   0% /var/lock
procbususb             10M   96K   10M   1% /proc/bus/usb
udev                   10M   96K   10M   1% /dev
devshm                316M     0  316M   0% /dev/shm
lrm                   316M   18M  299M   6% /lib/modules/2.6.17-10-generic/volatile
charlie@charlie-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3e0c0657-240b-45ed-ac0d-2e47dbc004b8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=50c35e8c-9fbd-42f7-91e1-adc89307f37e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by logos34 on 2007-01-18
Hope this helps.

**I Plug in My USB Stick and Nothing Happens** 

When a USB stick is plugged in, it must be mounted before you can access it. This normally happens automatically, and you should see an icon on your desktop similar to that displayed in Figure 6-8.

Unfortunately, in some rare cases it doesn't work. To fix it, first check that your system is set to automatically mount USB sticks. Click System > Preferences > Removable Drives and Media and look in the Storage tab. The following checkboxes should be selected:

Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

When you have selected the boxes, click Close, and try plugging your USB stick in again.
If you still have no luck, plug the USB stick in and then click PlacesComputer. If there is an additional drive in the Computer window, right-click it, and select Mount Volume.

If you still have no luck, you need to manually mount the disk. First, click Applications > Accessories > Terminal, and then plug in your USB stick. Now run the following command:

foo@bar:~$ sudo mount -t vfat /dev/sda1 /mnt

To view your files use the file manager to access the /mnt directory. Before you finish with the disk, unmount it with:

foo@bar:~$ umount /dev/sda1

Tip: Drive Names
On some computers you may need to use /dev/sdb1 or /dev/sdc1. Type in the following command when you have plugged in your disk to see which drives are available: 
foo@bar:~$ ls -l /dev/sd*

(source: The Official Ubuntu Book)

---

### Post by Charlie Wilkes on 2007-01-18
[QUOTE=logos34;2033468]Hope this helps.

Thanks, but no cigar.  It tells me the special device is not found, and when I try the wildcard search it says file not found.

---

### Post by pistcivet on 2007-01-18
I resolved my floppy mounting woes by changing a line in /etc/fstab:
/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0


If this doesn't mount the USB drive:
sudo mount -t vfat /dev/sda1 /mnt

Try this instead:
sudo mount -t vfat /dev/sda /mnt

Then see if you can browse the drive under /mnt

Depending on how the drive was formatted, sda1 may not work.

BTW, I format my USB drives so:```
sudo mkfs.vfat -I -c -v -n LABEL /dev/sda
```
the -I means "The  filesytem  can  go directly  to  the whole disk.  Under other OSes this is known as the ’superfloppy’ format." - (from man mkfs.vfat)

Any down side to this?

---

### Post by Charlie Wilkes on 2007-01-19
[QUOTE=pistcivet;2033702]I resolved my floppy mounting woes by changing a line in /etc/fstab:
/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

If this doesn't mount the USB drive:
sudo mount -t vfat /dev/sda1 /mnt

Try this instead:
sudo mount -t vfat /dev/sda /mnt

Thanks.  I made some progress with the floppy... the led on the drive lights up, and the system says it is "Opening 'Floppy 1'", but then after about 15 seconds it says "Unable to open" with the following details: "mount: block device /dev/fd0 is write-protected, mounting read-only

mount: /dev/fd0: can't read superblock"

(The disk is not write protected.)

Unfortunately I had no luck whatsoever with the flash drive.  Whether I specify sda1 or sda, the system says there is no such device.

Charlie

---

### Post by Charlie Wilkes on 2007-01-19
](*,) I just opened my computer's case to make sure I wasn't dealing with a hardware issue, and indeed that is what I found to be the case... loose cables.

My apologies for wasting peoples' time.

Charlie

---

