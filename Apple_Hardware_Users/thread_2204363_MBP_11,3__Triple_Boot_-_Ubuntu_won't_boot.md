---
title: "MBP 11,3  Triple Boot - Ubuntu won't boot"
date: 2014-02-08
forum: Apple Hardware Users
---

### Post by ben-bcchang on 2014-02-08
I have a 15" MBP retina display (11,3) that I'm setting up to triple boot OSX, Windows 7, and Kubuntu.  I installed ReFind, and installed Windows 7 using Bootcamp Assistant.  I installed Kubuntu, 64 bit, regular ISO.  

My partitions look like this:

```

GUID Partition Table detected.

Partition    Start Sector    End Sector  [COLOR=#008800]*# of Sectors System*[/COLOR]
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         409,640   941,221,823   940,812,184 Hierarchical File System Plus [COLOR=#666666]([/COLOR]HFS+[COLOR=#666666])[/COLOR] partition [COLOR=#666666]([/COLOR]Mac OS X[COLOR=#666666])[/COLOR]
/dev/sda3     941,221,824   942,491,359     1,269,536 Apple Boot partition [COLOR=#666666]([/COLOR]Mac OS X[COLOR=#666666])[/COLOR]
/dev/sda4     942,491,648 1,454,491,647   512,000,000 Data partition [COLOR=#666666]([/COLOR]Windows/Linux[COLOR=#666666])[/COLOR]
/dev/sda5   1,454,491,648 1,921,441,791   466,950,144 Data partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]
/dev/sda6   1,921,441,792 1,954,209,791    32,768,000 Swap partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]

```

sda1 is the EFI boot, SDA2 is the main OSX partition, sda3 is the OSX recovery partition, sda4 is my WIndows 7 partition, and sda5 is my kubuntu partition.

I can boot to OSX and Windows from Refind.  When I try to boot the Linux partition, I get a penguin logo for a little bit, then a black screen and blinking cursor, then it boots Windows.  Sometimes I briefly see a "No operating system found" message.

Here is the output from boot-repair:

[http://paste.ubuntu.com/6895503/](http://paste.ubuntu.com/6895503/)

I'm confused about whether I need to create a hybrid partition table, or what; I figured out how to do this on my last MBP 4 years ago, but everything seems a little different now.  

Also, all the text is so tiny on this ridiculously hi-res screen that I can't read what I'm typing.  I need a magnifying glass to read stuff on my computer monitor now.

---

### Post by ben-bcchang on 2014-02-08
Nevermind, I solved it :)
Used boot-repair, in Advanced, checked the option to install the bootloader to /boot/EFI
I think I accidentally skipped that step during the install
Now everything works.

---

