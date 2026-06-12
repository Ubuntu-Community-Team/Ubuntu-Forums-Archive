---
title: "Configuration not sticking"
date: 2008-12-09
forum: Apple Hardware Users
---

### Post by Craigular.B on 2008-12-09
Hello....My name's Craig, and this is my 2nd post here.

I recently upgraded my Ubuntu installation on my MacBook Pro (Intel, 4,1), and then ran the software update to update the packages. I was running 8.04 and had everything working (wifi via Ndisrapper, full multitouch via xorg.conf for synaptics), and updated my distro with the update manager to 8.10.

Unfortunately, after the updates (I did add the Mactell PPA source) (which installed an update to the bcm5974 for the trackpad via the Mactel PPA source), my configurations are not entirely being kept.

For example, when I enable the wireless drivers in Hardware Drivers (the Broadcom STA driver), it works until I reboot. Once I reboot, it says "activated but not in use) and I can't connect to any wireless networks. No amount of enabling and rebooting keeps the settings.

Also, my trackpad sporadically works (the multitouch, anyway). At first I downloaded and used the "appletouch.fdi" file and put it in the /etc/hal/fdi/policy directory, and it worked for a while. However, then tap-clicking and "right-clicking" w/ 2 fingers doesn't work. I also then tried using the 11-x11-synaptics.fdi in the same directory (all of this is from this thread: [http://ubuntuforums.org/showthread.php?t=977987]("http://ubuntuforums.org/showthread.php?t=977987")). However, I still can't right-click (or tap-click).

When I use the command ```
ls -l
``` in that directory, it says that there's an "appletouch.fdi~" file still there, but I can't get rid of it (at least not by renaming; I backed up my original appletouch.fdi by renaming to appletouch.fdi.bak in the same directory and deleting appletouch.fdi, and I can't rename the .fdi~ file).

Anyone have any suggestions on how to actually make these changes stay? I've been thinking about doing a full reinstall (after I remove my Windows Bootcamp partition since I hardly EVER use it), but I'm not sure if that would solve the problem or if there's an easier way to do it.

Thanks for your help!
-Craig

**Ok, so I just looked at the Mactell PPA support page, and it says that bcm5974-dkms is not needed unless I have a unibody MBP (which I don't). Should I uninstall this module? This is what the software update installed when I first ran updates.**

---

### Post by cyberdork33 on 2008-12-11
> **Craigular.B said:**
> For example, when I enable the wireless drivers in Hardware Drivers (the Broadcom STA driver), it works until I reboot. Once I reboot, it says "activated but not in use) and I can't connect to any wireless networks. No amount of enabling and rebooting keeps the settings.
have you blacklisted the b43 driver so that it does not load and try to drive your hardware?

> **Craigular.B said:**
> **Ok, so I just looked at the Mactell PPA support page, and it says that bcm5974-dkms is not needed unless I have a unibody MBP (which I don't). Should I uninstall this module? This is what the software update installed when I first ran updates.**I don't think it matters (the code for your machine is in there too), but I would try to get a response from kosumi on that one.

---

### Post by Craigular.B on 2008-12-11
Yea, I had the b43xx blacklisted (as per instructions in Ndiswrapper), but last night I ended up wiping the partition and reinstalling from the CD instead of upgrading from within the OS.

I haven't tried the WiFi drivers yet (since I have wired networking in my dorm and don't want conflicts between wired and wireless to deal with), but the trackpad works now; it hasn't even prompted me to download the bcm5974-dkms package yet, even though I've added the Mactel source and updated the package manager.

Reinstalling wasn't that big a deal because I didn't have anything personal on there and only minor configuration changes. The hardest part was backing up and restoring the Windows MBR during install so it didn't get trashed and not boot, but even that wasn't hard (I followed the guide I used to install Hardy over the summer for the MBR part).

---

### Post by cyberdork33 on 2008-12-12
> **Craigular.B said:**
> Yea, I had the b43xx blacklisted (as per instructions in Ndiswrapper), but last night I ended up wiping the partition and reinstalling from the CD instead of upgrading from within the OS.
bcm43xx is not the same driver as b43. You need to make sure b43 is blacklisted.

> **Craigular.B said:**
> the trackpad works now; it hasn't even prompted me to download the bcm5974-dkms package yet, even though I've added the Mactel source and updated the package manager.
It shouldn't. The package Ubuntu uses is "bcm5974". The package manager considers "bcm5974-dkms" a different package (but it replaces the other).

---

### Post by Craigular.B on 2008-12-12
> **cyberdork33 said:**
> bcm43xx is not the same driver as b43. You need to make sure b43 is blacklisted.


It shouldn't. The package Ubuntu uses is "bcm5974". The package manager considers "bcm5974-dkms" a different package (but it replaces the other).

Odd. It had pulled up the dkms package the first time I upgraded to Intrepid...Wonder if that's part of the problem.

I will be sure to blacklist the b43 driver, as well. Thanks!

-Craig

---

