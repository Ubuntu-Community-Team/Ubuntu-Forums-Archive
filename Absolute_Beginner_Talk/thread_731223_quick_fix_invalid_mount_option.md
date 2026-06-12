---
title: "quick fix? invalid mount option"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-03-21
Hi, I plugged in my Pen Drive into one Ubuntu machine to transfer some files to another, brand newly installed ubuntu mchine and got a "invalid mount option".  I've searched the forums and everything seems to be for CD/DVD mounting, not usb sticks.

It was with the automount feature.  I'm pretty clueless as to what to do.  This was before any updates or anything was installed.

If anyone could point me to a resource to fix this, I'd appreciate it

*edit* I should have mentioned, I CAN mount it manually using mount /dev/sda1 /usb

---

### Post by herbster on 2008-03-21
What filesystem is the pen drive?

---

### Post by dollraves on 2008-03-21
> **TJCIB said:**
> Hi, I plugged in my Pen Drive into one Ubuntu machine to transfer some files to another, brand newly installed ubuntu mchine and got a "invalid mount option".  I've searched the forums and everything seems to be for CD/DVD mounting, not usb sticks.

It was with the automount feature.  I'm pretty clueless as to what to do.  This was before any updates or anything was installed.

If anyone could point me to a resource to fix this, I'd appreciate it

*edit* I should have mentioned, I CAN mount it manually using mount /dev/sda1 /usb

I'm having the same problem with my 32 GB ATA Compact Flash card not mounting on my Fujitsu u810.  I can see it from the GUI "Computer - File Browser" window, but it shows as unmounted and trying to open or mount it gives me this error:  "Invalid mount option when attempting to mount the volume."
 
How do I find the device identifier to try to mount it manually?

Thanks,
-Carlota

---

### Post by herbster on 2008-03-21
First off, have you fellas been pulling them out of Windows boxes without hitting "Safely Remove Hardware"? This is the cause of these issues almost every single time.

To find out where it's at, you can use

```
sudo fdisk -l
```

And you should see it, noting the size of it.

---

### Post by dollraves on 2008-03-21
> **herbster said:**
> First off, have you fellas been pulling them out of Windows boxes without hitting "Safely Remove Hardware"? This is the cause of these issues almost every single time.

Not I, sir!  I haven't got a single windows machine.  This CF disk is brand spanking new, removed from packaging today.  I don't have a CF card reader for my Mac, alas, or I would have tried reformatting it.


> **herbster said:**
> 
To find out where it's at, you can use

```
sudo fdisk -l
```

And you should see it, noting the size of it.

Thanks!  I see it, it's pre-formatted I think... for System, I see "W95 FAT32 (LBA)"... I assume that's a windows formatting.

I guess it's time to learn how to format things using linux. ;)

---

### Post by TJCIB on 2008-03-21
The stick is FAT32

I didn't pull it out of a windows machine, I actually had just unmounted it from another Ubuntu box that it worked on.

doing fdisk -l doesn't show me the stick or its partition.  I only get hda1.  Interesting

---

### Post by herbster on 2008-03-21
> **dollraves said:**
> I guess it's time to learn how to format things using linux. ;)

In terminal, you can use:

```
sudo cfdisk /dev/xxx
```

"xxx" = sda1, etc. whatever the device is from your fdisk output.

For a GUI option you can use gparted, which should be in System > Admin > Gparted. Or ALT+F2 and input "gksudo gparted" hit ENTER. If you get nothing you don't have it installed, just do

```
sudo apt-get install gparted
```

> **TJCIB said:**
> The stick is FAT32

I didn't pull it out of a windows machine, I actually had just unmounted it from another Ubuntu box that it worked on.

doing fdisk -l doesn't show me the stick or its partition.  I only get hda1.  Interesting

TJCIB, plug the drive in and do nothing else, immediately paste the output of

```
dmesg
```

Only the end (last 20 lines or so) are necessary.

---

### Post by TJCIB on 2008-03-22
Thanks for the tip herbster.  I found the problem in dmesg.

the box was installed from a LiveUSB, and the fstab had /dev/sda as a cdrom0 and my actual cdrom as cdrom1 on /dev/hdc

I am assuming that the cdrom0 is from the computer that I used to put ubuntu on the USB

I removed the line from fstab and it automounts perfectly now.

Thanks

---

### Post by herbster on 2008-03-22
Great, mark the thread as solved for others :)

---

