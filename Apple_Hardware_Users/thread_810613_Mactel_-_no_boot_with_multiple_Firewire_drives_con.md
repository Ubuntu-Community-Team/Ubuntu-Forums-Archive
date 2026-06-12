---
title: "Mactel - no boot with multiple Firewire drives connected"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by zizou007 on 2008-05-28
I am dual-booting Ubuntu 8.04 and MacOS X 10.5.2 on a 1st generation Mac Mini (1,1), using rEFIt to switch OS's at startup.  I have a total of 4 external drives attached - 2 USB and 2 Firewire (FW) connected in series (the Mini only has one FW port) - all formatted HFS+ for Mac-side compatibility.  

I successfully installed Ubuntu on the main HD from the LiveCD, after partitioning via Boot Camp, and using [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook") for guidance.  This install was completed without any of the external drives connected so the problem did not appear until after things were up and running.  With the two Firewire drives connected in series, the boot process stalls after rEFIt turns things over to GRUB.  The screen goes completely blank and reports 'No Signal'.  This state persists for several minutes, at which point the system reboots itself.  

The system boots fine with just one firewire drive connected.  If I disconnect the second FW drive before rEFIt hands control over to GRUB, GRUB will run properly, and the first thing I see on the screen is GRUB...stage2.  Once I see that, I can reconnect the second drive, and the rest of the startup sequence will complete successfully.  

The same behavior occurs when I try to boot off the LiveCD with the FW drives attached, occurring at the same point.  I tested the LiveCD setup on my MacBook Pro (3,1), using the Option-key at boot to select my OS.  It detected the LiveCD, and allowed me to choose it, but with the FW drives connected, it hung on the OS selector screen (though interactivity had ceased.)  Attempting to start the LiveCD on the MBP using c on startup stops at the usual Mac startup gray screen (before the Apple appears.)  

Other things of note: (including those w/debatable relevance):
[LIST]
[*]Tried re-installing Ubuntu with all drives attached (starting up using the disconnect/reconnect method above)
[*]Tried running rEFIt's Partition Manager with all drives attached, and making sure the MBR is synched, which they are
[*]MacOS X boots with all drives attached
[*]Tried enabling/Disabling Journaling on the external drives
[*]Added all drives to fstab and given them permanent mount points
[/LIST]
It seems to me that it has either to do with GRUB's Stage 1 or how Apple's EFI manager handles passing discovered hardware information over to GRUB.  Either way, I am unsure what else to try, and would appreciate any and all suggestions.

---

### Post by cyberdork33 on 2008-05-28
I would assume that it is an issue with something Apple has done. the way that drives are viewed by the system is kind of different from most PCs. (example: on a Mac Pro, if you install Ubuntu to a second hard drive, after booting, the drive that you booted is always seen as the primary hard drive no matter the physical location.)

I am actually more suprised that rEFIt works OK with all that connected. I often have problems if I have certain drives connected via USB... (iPod is one of them). 

My guess is this. Grub is trying to pass control to your Ubuntu partition, but the Firewire drives are somehow confusing it... maybe reinstalling grub when all the drives are attached will yield different results (of course then it may have problems when they are not connected.)

This is a pretty unique problem, and if anyone is going to be able to fix it, it will probably be the Grub devs, if they can even figure out what the problem might be.

---

