---
title: "Grub Error 17 when removing USB drive"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by saracen on 2007-05-26
I installed Ubuntu from the LiveCD and at the time I had my external USB hard drive plugged in.  I noticed the other day that if I try and boot the machine without the USB drive plugged in then I get a Grub Error 17 before even seeing the boot menu so I can't boot into anything.  If I plug the USB drive back in and reboot then all goes well...

How can I fix this?

---

### Post by joramdam on 2007-05-26
I am no expert, but it sounds like Grub have ended on your eksternal HD. Hope omeone correkt me if i am advice you something stupid/fatal.. Unplug the ext HD. Boot with your win cd, and go to console and write fixboot and after that fixmbr. And windows shall boot as normal. Install Ubuntu with the ext HD unplugged, or follow the partition managers advise carfully ;)

---

### Post by saracen on 2007-05-26
No grub is not on my external hard drive because when I boot without the drive plugged in I am getting a grub error, so grub is installed on the proper drive.  It must be something to do with the drive mappings.  I tried reinstalling without the usb disk plugged in but I get the same error when I reboot - error 17.  It's only when I plug in the external drive it works... :(

---

### Post by confused57 on 2007-05-26
You might want to open a terminal(Applications---Accessories---Terminal), and post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list...you probably just need to post the boot entries

```
gedit /boot/grub/device.map
```

---

### Post by joramdam on 2007-05-26
Can you see the grub menu at all ?

---

### Post by saracen on 2007-05-27
I fixed the problem.  I wasn't seeing the grub menu at all and was getting Error 17.  I couldn't press 'e' to edit grub or do anything.  To solve it this is what I did:

1. Entered into my bios and noted down the sequence that the BIOS had my drives listed.  I have 4 drives - 2 IDE, 1 SATA and 1 SCSI
2. Booted with a liveCD and then mounted the root of my Ubuntu install on /media/disk
3. Then I ran sudo fdisk -l and noted where each of my drives was getting mapped under /dev
4. I went into the device.map file of my install which was under /media/disk/boot/grub/device.map and made sure that the hdX drives corresponded to the correct drives under /dev.  It turned out that the mapping was wrong - my SCSI and SATA drives were switched.  I changed it from:```
hd0 /dev/hda
hd1 /dev/hdb
hd2 /dev/sda
hd3 /dev/sdb
```To the following:```
hd0 /dev/hda
hd1 /dev/hdb
[B]hd2 /dev/sdb
hd3 /dev/sda[/B]
```
The hdX drives have to be in the same order as they are listed in your BIOS.  The third drive in my BIOS (hd2) was my scsi which was getting mapped to /dev/sdb when I booted the liveCD.  The reason it worked when I had the USB Drive in is because the BIOS was inserting it before the SCSI, which then bumped the SCSI down to being the 4th drive (hd3), so the mapping would then be correct.

This was kind of tough to track down... for someone who has no experience at all it would be a showstopper.  This could definitely be improved.

---

