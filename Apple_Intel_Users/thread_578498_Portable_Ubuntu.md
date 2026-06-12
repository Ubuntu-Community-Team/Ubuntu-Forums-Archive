---
title: "Portable Ubuntu"
date: 2007-10-17
forum: Apple Intel Users
---

### Post by rdb78 on 2007-10-17
This is what I'm trying to do:

Install Ubuntu on an external 20GB USB hard drive, which is bootable and usable from a windows machine, or a mac mini.  The internal hard drives of those machines do not get touched.

So far I have:
1) Using the windows laptop, I installed ubuntu to the USB hard drive, and was able to get it to boot.  It works great with this machine.  You plug in the usb drive, reboot, and you have ubuntu running.

2) On the Mac side, just plugging in the drive and using the option key doesn't recognize the drive, so for the time being I made a rEFIt boot CD, which does recognize the drive, and boots it.  However, the XWindow system doesn't start, and sometimes it doesn't even get that far.

I think the Ubuntu install on the usb drive was set up to expect the hardware on the laptop, and when it boots on the mac the hardware is all different.  I need some way to either set up different hardware profiles, or have it auto-detect the hardware at boot up.  The LiveCD works in both machines, so this should be possible somehow.

Any ideas how to set up hardware detection at boot up?


Thanks!

---

### Post by ItsMitsHere on 2007-10-23
Dear RDB78,

why dont you install ubuntu using mac machine, by live cd, and also you can try installing rEFIt on mac HD instead of using boot cd. I dont know perfectly how to do it but if you back up everything, you shoulden't be hesitating after little R&D.

Also if live cd works on both machines, how about checking the file system on live cd (there must be some i suppose!), and then formatting the usb drive with same partition system and copying the whole live cd content as it is on usb drive? this way it will be equivalent to live cd only!!!

---

### Post by eldepeche on 2007-10-25
If X is indeed the main problem, then you could set the driver to "vesa" in the Device section of xorg.conf . That way it won't try to load a driver that won't work. 

I think the Gutsy default xorg.conf doesn't include any specific modes (i.e. resolutions) and the driver tries to autodetect. That might keep you from using the optimal resolution on both machines.

I don't know what machine-specific stuff Ubuntu installs other than X though. This would be the biggest issue.

EDIT:

> **ItsMitsHere said:**
> Also if live cd works on both machines, how about checking the file system on live cd (there must be some i suppose!), and then formatting the usb drive with same partition system and copying the whole live cd content as it is on usb drive? this way it will be equivalent to live cd only!!!

This is a good idea. There are a lot of instructions for Ubuntu live USB installs on the web. Let us know what the results are.

---

