---
title: "USB drive not mounting"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by ijuba on 2007-09-06
Hi folks,

I have a seagate 100GB usb plug and play drive. I had repartioned it to ext3 format.
I'm having trouble mounting it though. I followed a very informative tutorial, which has been very helpful, until I get to the following:

issuing the following command as root:

/dev/sdb /home/don/Desktop/usbdrive ext3 users,noauto,uid=don,gid=users 0 0

I get this error:

bash: /dev/sdb: Permission denied


cd /dev

Then look at the permissions on sdb:

brw-rw----  1 root plugdev   8,  16 2007-09-06 10:03 sdb

Please help.

Thanks

---

### Post by mxg01 on 2007-09-06
The command you are entering looks like an fstab line.

If you want the drive to mount automatically on boot up then the line should go into your /etc/fstab file.

To edit it do this from a command line:

sudo cp /etc/fstab /etc/fstab.bak
sudo nano /etc/fstab

The first line makes a backup of the file. The second line starts the nano editor. Add your line at the bottom, don't worry about lining up the columns unless you want to.

Then you can reboot and hopefully the drive will be there.

---

### Post by ijuba on 2007-09-06
Hi mxg01,

Thank you very much for your reply, that has solved it. I just changed the permissions and am now able to access the drive and it's contents.

Cheers mate.

---

### Post by lishevita on 2007-11-04
This is SO not working for me.  Here's what dmesg has to say about my drive:

[ 9734.955635] usb 3-2: new full speed USB device using uhci_hcd and address 7
[ 9735.134541] usb 3-2: configuration #1 chosen from 1 choice
[ 9735.142596] scsi8 : SCSI emulation for USB Mass Storage devices
[ 9735.142724] usb-storage: device found at 7
[ 9735.142728] usb-storage: waiting for device to settle before scanning
[ 9740.138932] usb-storage: device scan complete
[ 9740.141921] scsi 8:0:0:0: Direct-Access     Motorola Motorola Phone   2.31 PQ: 0 ANSI: 2
[ 9740.147960] sd 8:0:0:0: Attached scsi removable disk sdb
[ 9740.148038] sd 8:0:0:0: Attached scsi generic sg1 type 0



And here's what happens when I try to mount:

$ sudo mount /dev/sdb /media/usb
mount: No medium found

Grrr...  Yes, my motorola phone works like a usb drive. It works fine on an older "xbuntu" system, and it works fine on a mac. It's not working on kubuntu feisty.   Any ideas?

---

