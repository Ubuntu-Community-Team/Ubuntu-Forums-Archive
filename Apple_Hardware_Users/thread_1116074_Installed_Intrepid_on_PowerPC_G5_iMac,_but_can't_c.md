---
title: "Installed Intrepid on PowerPC G5 iMac, but can't choose Linux to boot"
date: 2009-04-04
forum: Apple Hardware Users
---

### Post by jazzhead on 2009-04-04
Hi folks,

I have a PowerPC iMac G5 that I purchased in fall 2005. I just installed Intrepid on it. As far as I could tell, the installation went just fine.

I ejected the CD, restarted the machine -- and it booted into OSX without giving me a choice of operating systems.

So I restarted the machine again, this time holding down the alt key. Now I get a screen with a hard disk icon that has the OS X logo on it. The screen also has a refresh button and a right arrow button. Clicking the refresh button just brings up the same hard disk icon. Clicking the right arrow button boots the machine in OS X. 

Does anyone know how to select Ubuntu during the boot process?

Many thanks,

Jason

---

### Post by pmhauge on 2009-04-04
If it is just seeing your OS X partition when you boot into the startup manager, it sounds like your machine isn't seeing any Linux partition (ie, it wasn't installed correctly). 

Boot up into OS X then run the Disk Utility application (Applications/Utilities/Disk Utility). From there, you should be able to see if your drive has created any other partitions other than the one with OS X on it. 

Good luck!

---

### Post by tiresia on 2009-04-04
Did you use the LiveCD to install Ubuntu?
A G5 is 64-bit computer. When you start the installer, hit TAB and choose a 64-bit option

---

### Post by stream303 on 2009-04-06
A couple of questions - did you see any errors about yaboot complaining during install?

This isn't being installed onto an external firewire drive is it?

And did you shrink your existing osx partition (or reinstall osx to say half the drive) to allow for enough free space for Intrepid?

---

