---
title: "Can't boot OSX. HELP!"
date: 2009-05-03
forum: Apple Hardware Users
---

### Post by drewjurecka on 2009-05-03
I attempted to install Ubuntu Hardy Heron to an external drive from my Mac Pro.

Everything seemed to work fine, except that I am now unable to boot from my original OSX internal Hard Drive.  Boot camp, when run at startup, is recognizing my windows partition, but not my OSX drive.

I have since disconnected the Ubuntu-installed external and re-installed OSX.  Disk utility, when run from the OSX CD seems to find my OSX drive and think that the drive is in fine shape.  I have mounted the drive as an external on another computer and it seems to work just fine, so it seems like the Mac Pro can't find it as a viable startup disk for some reason, despite the fact that other than that the drive seems healthy in all other respects.

Any and all help would be greatly appreciated.

Thanks!

---

### Post by noice742 on 2009-05-03
Did you try to hold down the ALT key, when booting up?

---

### Post by cyberdork33 on 2009-05-03
you may need to sync your partition tables. you can use the refit CD to do this:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Until Jaunty, there was an odd bug that caused some partitioning issues on Macs. You should be using Jaunty, not Hardy for your install. It will make your life easier.

Additionally, installing to an external drive is not straightforward to get working properly, if at all.

Please see:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
AND
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by drewjurecka on 2009-05-18
Thanks for the help.
I ended up resolving the issue by zeroing out (a regular reformat didn't work) my OSX HD and doing a fresh install (I luckily have all of my data on a separate disk, so re-installing the system is no big deal), thus avoiding having to actually solve the problem.

I have since installed Ubuntu Studio Jaunty on a partition and it works fine.  You're right, jaunty is easier to deal with than Hardy.

The reason I was trying to install to an external drive is that I'm attempting to replace OSX with Ubuntu on an old macbook (intel 1,1) with a non-functioning CD/DVD drive.  I've had no luck installing from a USB key either (I get a black screen and a flashing white cursor, but the install won't load).  and for some reason it won't boot from an external drive.  I was trying to install to it in target disk mode.  (which I now realize won't work either)

Any recommendations? 
Thanks!

---

### Post by cyberdork33 on 2009-05-19
well the target mode install would work to get the system on the disk, but you would probably have to reinstall grub on that target machine somehow still. You could boot via EFI since you can get that all setup on the OSX side.

---

### Post by drewjurecka on 2009-05-19
strangely, after trying 2 different USB keys to no avail, I tried making a USB key installer on an SD card with an SD reader, and my computer successfully booted and loaded from that.

who knows why, but it worked, so I'm all set.

Thanks again for all the help.

---

