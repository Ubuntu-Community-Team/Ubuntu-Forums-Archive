---
title: "Unable to mount external drive"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by GLDM on 2007-11-04
Hello,
Just installed Ubuntu this morning and it went extremely smoothly.  The only issue is that I have an external  Seagate 400GB USB drive, that is a bit of a challenge.  Any help you could provide will be EXTREMELY appreciated :)

When I go to Places/Computer I can see the drive as Generic STORAGE DEVICE with a USB icon.  When I double click I get the message "Unable to Mount Media.  There is probably no media in the drive".
When I right click and go to properties and enter the mount information manually in the drive tab, it still does not work.
I tried mounting manually through Terminal but to no avail.

This is what I know:
1.  The drive is listed in lsusb
2.  sudo fdisk -l lists the drive as sdb1
3.  The directory sdb1 appears under dev (is that important?)
4.  Using GParted I see the drive and that it has 372GB occupied
5.  The drive is FAT32 based on testdisk

Once again...thanks.

GLDM

---

### Post by Harpoon on 2007-11-04
I haven't had this problem in a long time, so I have forgotten some details.  But to get you started, this is what I either know or think I know.
The usb drive **should** mount automatically.  Cheap and dirty solution is to unplug the device, wait a couple of seconds, and plug it back in again.  If all goes well you should have an icon on the desktop, and be able to read/write with no problems (since it is fat32).  If that doesn't work, try rebooting the computer without the device attached, and activate it after you have logged in.

I don't get why it should be mounted in /dev.  You can try creating a mount point in /media, which is where hal should be putting it automatically.

hope this helps a little.

---

### Post by kyphi on 2007-11-05
Try this:

Go to System, then Administration, then Users and Groups.

Click on your username entry which will make Properties accessible to you.

Click on User privileges and place a tick next to 'Enable access to external storage devices automatically'.

Then exit by clicking OK.

---

### Post by elctb on 2007-11-05
I use the following command:

sudo mount -t msdos /dev/sdb1 /mnt/

You might need to use a different file system type than msdos if that's not what's in your drive.

---

### Post by Harpoon on 2007-11-05
I did some searching and came up with something you might want to keep as a reference.  It covers a bit more than your question calls for, but useful:

[http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/](http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/)

---

### Post by GLDM on 2007-11-05
Hi,
unfortunatly these did not work.  here is 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59a57e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    c  W95 FAT32 (LBA)


The device is question is sbd1.  

When I try  sudo mount -t msdos /media/sdb1 /mnt/ 

I get 

mount: /media/sdb1 is not a block device


please help, I need access to my files :-(

---

### Post by dfreer on 2007-11-05
it should be /dev/sdb1 and not /media/sdb1. /dev/sdb1 is the actual device, whereas /media/sdb1 is a folder, that if you so choose you can mount /dev/sdb1 to. For example, I can have /dev/sda1 mount to /home/daniel/myexternalusb if I wanted to.

EDIT: Really though, you shouldn't need to use a command to mount your external USB drive, it should just work. Unplug the USB drive and then turn it off, reboot ubuntu, and login. From there, turn on the USB drive, wait a few seconds and then plug it into your computer. If you don't see an icon on your desktop, open up a terminal and post the output of the following three commands:
```
dmesg | tail
sudo fdisk -l
cat /etc/fstab

```

You already posted the output of fdisk -l once, but since it's an USB device, it's possible for it to get a different name like /dev/sdc1, /dev/sdd1 etc. This can happen sometimes, generally if:
(1). Your USB drive gets disconnected, then reconnected.
(2). Another USB drive is plugged in, like a thumb drive.

---

### Post by GLDM on 2007-11-06
Thank you guys for all your help.

Another thing I saw is that after I rebooted while the drive was disconnected it still showed up under computer.  In any case it still didn't work.

Here are the outputs from the commands:

dmesg | tail
[  259.267783] CCMP: received packet without ExtIV flag from 00:16:b6:2e:80:7f
[  259.271460] CCMP: received packet without ExtIV flag from 00:16:b6:2e:80:7f
[  259.281752] CCMP: received packet without ExtIV flag from 00:16:b6:2e:80:7f
[  259.285334] CCMP: received packet without ExtIV flag from 00:16:b6:2e:80:7f
[  259.292323] CCMP: received packet without ExtIV flag from 00:16:b6:2e:80:7f
[  259.296939] CCMP: received packet without ExtIV flag from 00:16:b6:2e:80:7f
[  259.300852] CCMP: received packet without ExtIV flag from 00:16:b6:2e:80:7f
[  259.305126] CCMP: received packet without ExtIV flag from 00:16:b6:2e:80:7f
[  274.628424] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[  306.616652] usb 5-1: reset high speed USB device using ehci_hcd and address 8

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdf: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59a57e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       48641   390708801    c  W95 FAT32 (LBA)

cat /etc/fstab

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=6cbf601e-a5e0-409b-8c9e-b4708a113338 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=bcf57058-a200-43ff-838f-68a14157e6d6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0


Thank you once again.

---

### Post by dfreer on 2007-11-06
See, now for some reason it is mounted as /dev/sdf1. Hmmm, try installing the pmount package, if it's not installed already:
```
sudo apt-get install pmount
sudo adduser `whoami` plugdev
```
Check your **System > Preferences > Removable Drives and Media**, and check and see if the following options are selected:
Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

Restart, unplugging your external from your computer once again. Log back in, and try the automatic mount one more time by plugging in your external drive.

After that, if it still doesn't mount automatically, type in the following command (check your fdisk -l command again, and make sure it's still at /dev/sdf1. If it changed (like if you've rebooted since then), just replace the name in the command appropriately):
```
pmount /dev/sdf1
```

It should mount your external hard drive in a folder of it's name in /media/, and you should have a shiny new icon on your desktop to mount/unmount it from. Hopefully, this should take care of your mounting issue. Let us know!

---

### Post by GLDM on 2007-11-07
Hi,
I installed pmount, but I don't think it helped.  I got a second mention of a device under computer but it disappeared after the reboot.   I also changed the command you gave me to sdb1 since that is what fdisk said after the reboot.  Here is sudo fdisk -l again.

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59a57e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    c  W95 FAT32 (LBA)

---

### Post by elctb on 2007-11-07
Your usb drive is using fat32. Therefore, you need to specify the vfat file system type to the mount command, try:

sudo mount -t vfat /dev/sdb1 /mnt/

---

### Post by GLDM on 2007-11-08
ONE STEP CLOSER... :-)

OK...so now I can see the content of the drive if I drill down to /media/sdb1.  So now the remaining challenge is to make it appear under computer and make it a appear automatically as a USB device.

---

