---
title: "Stuck on apple logo"
date: 2012-03-13
forum: Apple Hardware Users
---

### Post by godelski on 2012-03-13
So I'm trying to install Ubuntu onto my Mac Mini from a usb.  I followed Ubuntu's formal documentation and when I tried to boot from the usb it gave me the legacy error.  Well I read that that was a problem here, [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation), so I used the code ```
bless --device /dev/disk1s1 --setBoot --legacy
``` I used diskutil list to see that my usb was disk1s1.  Now that I've done that when I reboot I am just staring at the apple logo.  It use to start with rEFIt and I could try to boot from the usb or boot OSX from the hdd.  

I don't even know where to start now because all i can do is stare at the white screen with the apple logo and it cycles with a null sign.

I would greatly appreciate it if anyone could help me out.

---

### Post by Xertia on 2012-03-13
Try holding Alt when you boot up then choose rEFIT

---

### Post by godelski on 2012-03-16
I've tried holding alt, alt+c, command, command+c, c, and other various key combinations.  The problem happens with or without the live cd plugged in.  rEFIt does not show up at all.  I can not boot from the usb drive.  I actually think something is wrong with the EFI, but I don't really know anything about it.

And I can't take it into the Apple store till Sunday because of the IPad launch.

---

