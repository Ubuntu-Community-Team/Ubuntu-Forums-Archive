---
title: "External USB disks - changing mount point"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Robert Leithe on 2006-11-24
Hi,

I have three external USB disks.
Two of them recently formatted under Ubuntu 6.10, the last one is still NTFS.

The two first mentioned (one ext3 the other fat32) are shown as usbdisk and usbdisk-1.
However, on every boot (so far), which disk displays as usbdisk and which displays as usbdisk-1 changes. For example, the Maxtor disk will be usbdisk, and the Western Digital will be usbdisk-1 one day. The other day, Maxtor will be usbdisk-1 and WD usbdisk. Only to be changed back on the third day.

How can I have the same disk mounted (if that's the proper use of word in this scenario) as the same name every time?

Sincerely

---

### Post by bodhi.zazen on 2006-11-24
> **Robert Leithe said:**
> Hi,

I have three external USB disks.
Two of them recently formatted under Ubuntu 6.10, the last one is still NTFS.

The two first mentioned (one ext3 the other fat32) are shown as usbdisk and usbdisk-1.
However, on every boot (so far), which disk displays as usbdisk and which displays as usbdisk-1 changes. For example, the Maxtor disk will be usbdisk, and the Western Digital will be usbdisk-1 one day. The other day, Maxtor will be usbdisk-1 and WD usbdisk. Only to be changed back on the third day.

How can I have the same disk mounted (if that's the proper use of word in this scenario) as the same name every time?

Sincerely

Easiest way is to use labels and add an entry in [fstab](http://www.ubuntuforums.org/showthread.php?t=283131)

You then moun/fstab with LABEL=xyz

Examlpe I use in fstab:
> LABEL=usb /media/usb auto noauto,users 0 0This is for a USB device with jfs.

Now to mount:```
mount /media/usb
```OR```
mount LABEL=usb
```

See the fstab link for how to label and add an entry for fstab...

---

### Post by Robert Leithe on 2006-11-26
There's something I'm missing here... ](*,) 

I ran the e2label to label one of the USB disks (my Maxtor disk).

I have created these two lines in /etc/fstab
# /dev/sdc
LABEL=Maxtor /media/Maxtor ext3 defaults 0 0

You say "You then moun/fstab with LABEL=xyz", but all my USB disks automount on startup.

So at the moment, I'm still getting usbdisk and usbdisk-1

---

