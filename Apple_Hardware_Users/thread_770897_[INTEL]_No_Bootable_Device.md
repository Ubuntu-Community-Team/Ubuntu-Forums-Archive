---
title: "[INTEL] No Bootable Device"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by jxself on 2008-04-27
Using 1.83GHz Intel Mac mini (MA608LL/A.)

I downloaded 8.04 to try the live CD. I could not get it to boot by holding down the C button, so in OS X I changed the startup disk to the CD from inside System Preferences.

After booting up, I watched the Ubuntu video on the CD with Nelson Mandela, played with a few apps. That was it. I was quite happy with it, and decided to reboot back into OS X (Before I switch to Linux I need to replace my TV tuner with one that will work with MythTV.)

I made trip up to the menu, the CD ejected, and I was restarting.

I ended up at a black screen saying just "no bootable device -- insert book disk and press any key."

I have tried many different ways to boot with no success: I powered up while holding down the option key with the same result. I powered up, quickly inserted the Leopard DVD and held down the C button with the same result. I also tried Target Disk Mode (T on power on) and still encountered the same message.

I searched Google and these forums and found
[http://ubuntuforums.org/showthread.php?t=622328](http://ubuntuforums.org/showthread.php?t=622328)
[http://ubuntuforums.org/showthread.php?t=766074](http://ubuntuforums.org/showthread.php?t=766074)

Which refer to this message, but these are from people that have actually tried to install the OS (I never opened the installer.)

Since neither the option button nor the C button will work (and since the Leopard DVD is stuck in my drive now because holding down the mouse button does not make the Mac eject it on power on) I seem to be dead in the water.

I have no issue with erasing the internal drive, if needed, because I have a recent backup but at the moment I seem to be dead in the water.

---

### Post by jxself on 2008-04-27
Out of an experiment, I tried a different (older) Apple keyboard and using the option key worked. (I remembered that, when booting the Live CD, I wasn't able to select a language. Fortunately it defaulted to English so I just let it count down to zero.) It is interesting that there seem to be issues with Apple's wired aluminum keyboard.

---

### Post by cyberdork33 on 2008-04-27
> **jxself said:**
> Out of an experiment, I tried a different (older) Apple keyboard and using the option key worked. (I remembered that, when booting the Live CD, I wasn't able to select a language. Fortunately it defaulted to English so I just let it count down to zero.) It is interesting that there seem to be issues with Apple's wired aluminum keyboard. Although there are several known issues with the aluminum keyboards, the after effects of that are even stranger. In the future I wouldn't choose the cd as your startup device, but just hold option on startup to choose a bootable device. rEFIt might be handy if you plan to do this more as well.

Sorry that you had such an unpleasant experience.

---

### Post by Richardcavell on 2009-07-06
For the record, this error message indicates that the GPT and MBR tables are not synchronised. The solution to the problem is to use rEFIt's gptsync.efi utility, or else don't partition your Apple computer's hard disk using gparted in the first place.

Richard

---

