---
title: "Losing X with new kernel updates Macbook Pro"
date: 2008-04-12
forum: Apple Intel Users
---

### Post by rscow on 2008-04-12
Macbook Pro (first Gen)
Hardy Heron beta
I have the Beryl/Compiz/Emerald setup and running
ATI restricted driver installed

I am running the Hardy beta, and really have had very few problems.  The last two times I did upgrades, I experienced problems.  In each upgrade, there was a kernel update, from version -14 of the kernel to version -15 and then -16.

This is what happened:  Did the upgrade.  The new kernel was installed.  Restarted the machine.  Got the login splash.  Logged in.  Got the Hardy desktop picture.  Then the whole screen went Ubuntu brown, then white.  The cursor was still there.  But I can't select anything.  A control-alt-delete restarts the X server, and login again presents the same thing.  If I log into a terminal and then comment out the new kernel updates in /boot/grub/menu.lst the system restarts fine, and I have X working properly.

So, I think I have something in my X configuration that isn't liking the kernel updates, but I don't really know how to fix it.

Anyone able to help?

Thanks

Roger

---

### Post by cyberdork33 on 2008-04-12
the desktop is running, but it sounds like your ATI driver is not working (at least not the 3d part) and compiz starts, thus making the screen white. When it is all white, you can do ALT+F2 which brings up the "run" window in gnome, then you can type the command:
```
metacity --replace
```and press enter, then you desktop will appear. How did you install your ATI drivers? you need to update them to work with the new kernel.

---

### Post by rscow on 2008-04-12
I don't have my F keys working right it seems.  I un-commented the lines in /boot/grub/menu.lst to allow the newest kernels to show up for grub and restarted.  Same behavior, white screen.  So I hit Alt F2 and got nothing.  Had to control-alt-delete and restart.  Selected the -14 kernel in the grub menu.  

I compiled my ATI drivers from instructions here:  [https://help.ubuntu.com/community/MacBookPro#head-d358330c411813ea4c99412dbcf04126053aa259](https://help.ubuntu.com/community/MacBookPro#head-d358330c411813ea4c99412dbcf04126053aa259)

I am not sure how to recompile them if I can't successfully boot into the new kernel.  I will have to do some more work here, I see.

Roger

---

### Post by cyberdork33 on 2008-04-12
boot into the kernel that works and disable compiz (desktop effects) then you should be able to reboot into the latest kernel and see the desktop. 

You shoud have to compile fglrx. The version in the Ubuntu repo is great! Otherwise I would suggest using envy which will make deb packages to install, then they should upgrade with the kernel.

PS I think that you also have to hold the Fn on a Macbook to access F1, F2, etc. So it would be Fn+Alt+F2

---

