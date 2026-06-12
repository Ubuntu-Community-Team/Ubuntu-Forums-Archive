---
title: "Mounting and unmounting a zip drive"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-10-01
Hi,
I have floppy drive and zip drive on my old dell Optiplex GX 8 computer. I am using Xubuntu.

I inserted a brandnew zip disk (100 MB) to my zip drive and I want to use it for backup/data transfer purposes.
But I can not use it.

Here is my /etc/fstab file:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda7       /tmp            ext3    defaults        0       2
/dev/hdb5       /usr            ext3    defaults        0       2
/dev/hda5       /var            ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
~

I can access to /media/floppy0 folder and create some test files.
Then, I try to umount it.
I use the following command and got error mesage:
mozkaynak@ozkaynak:/dev$ sudo umount -l /dev/fd0
umount: /dev/fd0: not mounted

what is wrong here?

one possibility is fd0 is used by the 3.5 inch floppy disk drive.
Then how to activate 100 MB zip drive?
Before I bring the zip disk, I formateed it on a Windows machine with fat or vfat at office.

Any help will be highly appreciated.

---

### Post by bodhi.zazen on 2006-10-01
1. It appears your floppy is not mounted. If the drive is not mounted you can create and access files in the /media/floppy0 making it "appear" is is mounted.

To confirm this, type ls /media/floppy0 and look at the output.

Now mount the floppy and ls /media/floppy0.

2. In my experience zip drives appear much like other USB drives, ie sdxy. For some reason mine appears as sda4, why the 4 I know not.

Connect to the zip drive to the computer and put a disk in the drive.

Then type: [code]sudo fdsik -l]

This will give you the /dev/sdxy information you need to mount.
Then mount or add to fsab as you see fit.

---

### Post by mozkaynak on 2006-10-01
I run 
sudo fdisk -l

But it did ot give any info about my zip drive.

It gives info about my harddisks and my usb drive.
so where is my zip drive?

Thanks...

---

### Post by bodhi.zazen on 2006-10-01
Either:[list=number][*]You missed the information on your zip drive.[*]You do not have a disk in the drive.[*]Your zip drive is not working.[*]Or your zip drive is not recognized.[/list]

Only other thought is to disconnect your usb drive and re try fdisk -l.

---

### Post by bodhi.zazen on 2006-10-02
Try this link:

[[color=blue]How to Iomega Zip[/color]](http://doc.gwos.org/index.php/IomegaZip)

---

