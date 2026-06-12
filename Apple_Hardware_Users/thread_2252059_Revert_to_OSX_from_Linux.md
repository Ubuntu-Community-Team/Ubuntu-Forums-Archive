---
title: "Revert to OSX from Linux"
date: 2014-11-08
forum: Apple Hardware Users
---

### Post by Michael_Kolonay on 2014-11-08
I recently attempted to convert my old IMac to Ubuntu. I was able to install Linux without problems, and I chose to install it alone without a partition for OSX. Everything was fine until the power went out and the computer went to the selection screen instead of loading the operating system.  For some reason the Mac would not recognize any keyboard before the operating system would load, so I was effectively locked out. I was able to reenter Ubuntu using the instalation CD to skip the selection screen, but this was hardly a clean solution. The keyboard issue had already show itself during the conversion to linux in that I was unable to access the boot selection screen (I was forced to borrow my brother's Apple bluetooth wireless keyboard which turned out to be the only keyboard recognized by the computer during boot). 

At any rate, I have decided to revert my IMac to OSX. I have partitioned the drive as I believe I was supposed to: **Mac OS Extended (case-sensitive,journaled **and it is mounted at **/volumes/untitled. **Unfortunately, when I try to run the boot cd I am left with an error message: [B]Mac OS X cannot be installed on this computer.

[/B]The log further describes the error:
[B]localhost LCA[65]: Folder Manager is being asked to create a folder (cach) while running as uid 0
localhost LCA[65]: Folder manager is being asked to create a folder (asav) while running as uid 0
localhost OSInstaller[145]: Installation checks failed.
localhost OSInstaller[145]: Installation check failures: This software cannot be installed on this computer.
localhost OSInstaller[145]: Folder manager is being asked to create a folder (asav) while running as uid 0[/B]

Is there something more that I need to do besides formatting the drive to make the computer receptive to OSX?

---

### Post by reinhard-boris on 2014-11-10
Have another look at the OSX formatting tool (via boot from the OSX CD/ DVD; try resetting the PRAM via "alt" +"p" + "r" till another reboot happens and then pressing and holding the "alt" key right after the boot sound) and make sure to delete all partitions, also better to format the drive with *case insensitive* journaled as otherwise some programs will not work.

If you should still not be able to boot from the OSX CD/ DVD, use the live-boot CD/ DVD and when up set as many partitions as possible inactive and delete them, after that try again to boot from the OSX CD/ DVD and let the OSX tool handle the partitioning.

Hope this helps :)

---

