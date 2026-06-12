---
title: "Won't Boot"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Don1500 on 2007-05-03
OK, so far so good. installed ubuntu on my USB drive (126 Gig). but it won't boot. I get the error "Boot disk corrupted" 

How do I make this drive bootable? It happens on my laptop and my desk top.

Thanks,

Don

---

### Post by surfjdh on 2007-05-03
I almost got this to work
heres what you should try first reformat your usb to ext3 filesystem, then boot from the live cd, and select the usb drive as your install location, restart your comp when finished, hold either f8 or f6 at boot, or whatever shortcut your motherboard has for the boot menu and select the usb drive, it might work.  It didn't for me because i was using a usb2.0 drive on a usb1.2 port.....not very smart.

---

### Post by Don1500 on 2007-05-03
That's what I ended up doing. Perseverance will win. I have it working on the desk top, now to work on the laptop.

---

### Post by surfjdh on 2007-05-04
I got it to work this time, i just had to nuke the flash drive first and allow gparted to allocate the ext3, and swap partitions through the live cd environment.  and bam!! i have ubuntu everywhere i go now.  One problem though, because of all the millions of different hardware configs out there, you will have the xserver/xorg crash, this is easily rectified by typing this in console  sudo dpkg-reconfigure xserver-xorg and just blaze through that.  then when its finished. type startx.  coo? have fun.  oh btw i almost got my wii to boot ubuntu, need a grub it recognizes for the cd drive.....ill figure it out

---

