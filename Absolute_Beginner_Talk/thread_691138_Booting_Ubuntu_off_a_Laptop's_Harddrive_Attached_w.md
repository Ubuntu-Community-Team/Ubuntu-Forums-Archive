---
title: "Booting Ubuntu off a Laptop's Harddrive Attached w/ USB to a Desktop"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by neal.s on 2008-02-08
My laptop broke the other day. I'm buying a new laptop, but in the mean time I'd like to just boot right off of my laptop hard drive on another computer.

I plugged my laptop hard drive into a desktop computer using a usb adapter. I've got the desktop booting into my GRUB, but when I pick the Windows XP option, it just doesn't do anything.  When I pick the Ubuntu option in recovery mode, I can see the error

[COLOR="Red"]failed to access '/dev/disk/by-uuid/F0B087E2B087AE22'.[/COLOR]

I imagine even if I could boot up, I'd end up having to reconfigure all of my hardware settings. I'd also like some help with that.

---

### Post by dstew on 2008-02-08
> I'd like to just boot right off of my laptop hard drive on another computerWhat is on the laptop hard drive? Windows, Ubuntu, or both?> I've got the desktop booting into my GRUBIs this grub on your external hard drive, or on your desktop hard drive?

---

### Post by neal.s on 2008-02-08
The grub loader is from my laptop HD, which has a 35 gig Ubuntu partition and a 40 gig XP partition.

---

### Post by dstew on 2008-02-08
You will need to re-configure the grub menu because the disk now finds itself in a different environment. We can try to boot your Ubuntu system using the grub command line, because it seems you get to the grub menu OK. Reboot, and when the grub menu appears, hit 'c'. This will get you the grub command line, with the **grub>** prompt. On the grub command line, type```
root (
```then hit the tab key. It should give you a list of disks that grub can see, in the grub-style, like (hd0). Post what you get, and we can start there and explore the problem a little more.

---

### Post by neal.s on 2008-02-08
Thanks a lot for the help.

It told be that I have fd0 and hd0 available.

---

### Post by dstew on 2008-02-08
That is a bit odd. Doesn't your desktop have a hard disk?

Anyway, now enter on the grub command line```
geometry (hd0)
```This will list your partitions, so we can be sure which is the Ubuntu partition, and which is the Windows partition.

---

### Post by neal.s on 2008-02-08
In order to get the bios to boot from the USB hard drive I had to directly unplug it.

---

### Post by neal.s on 2008-02-08
Hi, my results were:

partition 0, ext2fs, type 0x83
partition 1, unknown, type 0x7
partition 2, unknown, type 0x82

Which is a little worrying, as there should be an ext3, an ntfs, and whatever the formatting of the swap part is.

---

### Post by dstew on 2008-02-10
I believe type 0x7 is ntfs, and type 0x82 is swap. See [this page]("http://www.win.tue.nl/~aeb/partitions/partition_types-1.html"). Remember, you are asking grub to look at the partitions, and it is not as capable as Linux.

It seems that (hd0,0) is your Ubuntu partition. From the grub menu, press 'e' to enable you to edit the commands that boot the external hard drive. Make sure that the root statment has the argument (hd0,0) The kernel line should probably have the root as /dev/sda1

---

