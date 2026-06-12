---
title: "USB drive doesn't mount?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Dandalf on 2008-01-11
what does:

[b]Cannot mount volume
Unable to mount the volume.

mount: wrong fs type, bad option, bad superblock on / dev/sdc1. missing codepage or helper program, or other error       in some cases useful info is found in syslog - try       dmesg | tail or so[/b]

mean? :(

I get it after plugging in my new 4gb USB key, or my k800i phone (usb also) when both worked perfectly before doing a bunch of updates recently. The updates also screwed my display drivers, but that's not what I'm asking (it always and without fail happens with Ubuntu, and this makes me angry)

Can anyone help me get my USB drives working again? :(

---

### Post by nikoPSK on 2008-01-11
> **Dandalf said:**
> what does:

[B]Cannot mount volume
Unable to mount the volume.

mount: wrong fs type, bad option, bad superblock on / dev/sdc1. missing codepage or helper program, or other error       in some cases useful info is found in syslog - try       dmesg | tail or so[/B]

mean? :(

I get it after plugging in my new 4gb USB key, or my k800i phone (usb also) when both worked perfectly before doing a bunch of updates recently. The updates also screwed my display drivers, but that's not what I'm asking (it always and without fail happens with Ubuntu, and this makes me angry)

Can anyone help me get my USB drives working again? :(

is it FAT or NTFS? they die easily....

Best,
nikoPSK

---

### Post by eapache on 2008-01-11
Do they work when plugged into windows?

---

### Post by nikoPSK on 2008-01-11
> **eapache said:**
> Do they work when plugged into windows?

that too.... :lolflag:

---

### Post by Dandalf on 2008-01-11
Yeah, they work in windows.

And, I don't know whether they're NTFS or FAT, I could find out in a few seconds, but "die easily"? Neither device has 'died', because they both work in windows, and both now return the same error only after 'updating' ubuntu.

Thanks for the swift reply guys :)

---

### Post by nikoPSK on 2008-01-11
> **Dandalf said:**
> Yeah, they work in windows.

And, I don't know whether they're NTFS or FAT, I could find out in a few seconds, but "die easily"? Neither device has 'died', because they both work in windows, and both now return the same error only after 'updating' ubuntu.

Thanks for the swift reply guys :)

by die easily I mean they sometimes don't mount properly. :lolflag:

---

### Post by eapache on 2008-01-12
Do you "safely remove" them in Windows? I know Ubuntu is picky about that, and will fail if they were unplugged "unsafely" last time.

---

### Post by Dandalf on 2008-01-13
Yeah, always safely removed :(

---

### Post by eapache on 2008-01-13
Try opening up a terminal (Applications>Accessories) after plugging one in and run the command it mentions. Perhaps the more detailed error message will reveal something important.

---

### Post by nikoPSK on 2008-01-13
does this show them?

```
lsusb
```

nikoPSK

---

### Post by Dandalf on 2008-01-16
i put lsusb in the console and got

daniel@daniel-desktop:~$ lsusb
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 002: ID 041e:4052 Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1307:0163  
Bus 002 Device 001: ID 0000:0000  
daniel@daniel-desktop:~$

it sees mouse, and webcam, i don't know what those others are but mouse and webcam are all i have plugged in so it makes sense (apart from the usb key of course)

---

### Post by nikoPSK on 2008-01-16
> **Dandalf said:**
> i put lsusb in the console and got

daniel@daniel-desktop:~$ lsusb
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 002: ID 041e:4052 Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1307:0163  
Bus 002 Device 001: ID 0000:0000  
daniel@daniel-desktop:~$

it sees mouse, and webcam, i don't know what those others are but mouse and webcam are all i have plugged in so it makes sense (apart from the usb key of course)

well, your system doesn't locate it... :confused:

---

### Post by bamboo_albion on 2008-01-18
Hi!
i have the same problem with this guy.
it is NTFS formatted and have 2 partitions.
just now can be mount but after i alter the mount point(if not mistaken but for sure at the disk properties) from umask=0222 to umask=0000.
before i altered it, i can mount it.but cannot eject the disk.
and now i can't mount it at all.
but they work properly with windows of course.
any advice?

---

### Post by Dandalf on 2008-01-28
bump!

---

### Post by jonspraggins on 2008-02-15
Bump indeed!  I have 2 usb drives that work perfectly with windows.  Even after "Safely removing" the drives, Ubunbu 7.10 reports "Cannot Mount Volume, Unable to Mount Volume"

---

### Post by xeth_delta on 2008-02-15
> **jonspraggins said:**
> Bump indeed!  I have 2 usb drives that work perfectly with windows.  Even after "Safely removing" the drives, Ubunbu 7.10 reports "Cannot Mount Volume, Unable to Mount Volume"

Please connect the device. Open a terminal, post the output of the following commands, between CODE tags:
```
lsusb
lspci
dmesg
```

---

### Post by greg.hagen on 2008-02-29
I have a similar problem. I get the "cannot mount volume" when plugging in any external hard drives, memory cards, etc.

However I can...
```
sudo mount /dev/mmcblk0p1 /media/mntdisk/
```
Where mmcblk0p1 is the device and mntdisk is a folder I created, and it works fine. WTF guys?

---

