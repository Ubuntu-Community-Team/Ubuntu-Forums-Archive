---
title: "Is there a way to do a &quot;repair installation&quot;?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-11-26
My Ubuntu installation works fine most of the time but freezes randomly and I can't figure it out.  Is it possible for me to do a "repair installation" like the WinXP option from an Ubuntu CD?

---

### Post by christina_svats on 2007-11-26
Have your internet connection up and running, back up your files (just in case), reboot in recovery mode and enter: 

apt-get install --reinstall sudo

I hope it helps, it probably won't affect your files, but do back up just to be sure.

---

### Post by Hospadar on 2007-11-26
not really, you could try re-installing critical packages like the kernel and whatnot, or really you could re-install all your packages (though it would take forever, and probably not do anything other than mucky things up)

Usually random freezes are caused by hardware incomaptibilities.

Try sequentially removing preipherals (mouse, keyboard, any usb devices, external drives) and see if any of them are the cause, also try disabling your video drivers.

Also try disabling services you don't really need (bluetooth, printer stuff, power saving) also have a look at your startup programs and see if there's anything you know you don't need (don't just kill stuff if you don't know what it is) System->Preferences->Sessions, System->Administration->Services

Worst case scenario, you can just backup your home directory, do a complete re-install and then copy your home directory back in.  that's pretty much the equivalent of a repair install (you'd need to re-install any extra packages you installed).  If you don't have a dvd burner or an external big enough, you can resize your main partition, move your homedir to a new partition, and then during installation, set that partition to be mounted as your home drive.

And just so you know, the above choices could be risky in terms of data, so be sure you have important stuff backed up somewhere you won't accidentally delete it (like a cd, or an external, or jump drive, etc)

---

### Post by AncientPC on 2007-11-26
Thanks.  I may end up wiping / reinstalling but I'm just delaying it as much as possible.

Hospadar: Not possible as the system in question is a laptop.  Sometimes I'll have an uptimes of days before it crashes, sometimes it'll happen more than a couple times within a single hour.

Likewise I've been rebooting into WinXP trying to see if it'll crash, but I get an uptime of 3+ weeks just fine. :(

---

