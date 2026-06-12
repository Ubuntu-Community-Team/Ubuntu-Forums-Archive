---
title: "ATI Radeon 3000 screen resolution."
date: 2011-06-01
forum: Any Other OS
---

### Post by WarrenL on 2011-06-01
Dear all,

I've just upgraded my motherboard and CPU to a Gigabyte  GA-MA78LMT-S2 and Athlon X2 255, and all went well except for the video driver. My Dell 1907FP LCD likes to run at 1280x1024, but I no longer have any option higher than 1024x768.

I've tried installing the proprietary drivers, but I end up even deeper in the poop, with no display after the boot splash screen. I'm forced to reboot in recovery mode, and use the low resolution mode to get back into the desktop then deactivate the ATI driver.

A nice gentleman posted something about ATI drivers here:

[http://ubuntuforums.org/showthread.php?t=1203437](http://ubuntuforums.org/showthread.php?t=1203437)

It looks a little relevant. Is it current enough? Should I give it a go?

Small confession: I'm running Mint 11, but I'm responsible for at least half a dozen Ubuntu converts from Windows, so I hope you'll allow me this one transgression.

Regards,
Warren

---

### Post by Yellow Pasque on 2011-06-01
I'd recommend this to get back to default configuration: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)

Then you can try installing the latest Catalyst from AMD if you wish: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)

---

### Post by WarrenL on 2011-06-01
Thanks Temujin. I should clarify that I've done a fresh install since I tried Catalyst, so it is no longer there and the system is clean.

In fact, at least one reason to do the fresh install was to get rid of Catalyst, since I seemed to be digging myself into a deeper and deeper hole (amply proving the old adage that a little knowledge is a dangerous thing) as the evening wore on.

I'm now a little scared of installing it again. Is it in actual fact the default driver that is restricting me to 1024x768?

Interestingly, I appear to be able to set the splash screen to 1280x1024 without problems.

---

### Post by WarrenL on 2011-06-02
Well, the problem is solved!

Temujin, I followed the instructions in your link to the letter, and ended up in the pooh again. No display. But wait! The message I was reading was "cannot display this resolution/mode" or similar, which I suddenly realised was from the monitor, not the PC. Was it simply the default display mode causing my problem?

So I brought a spare monitor home from work, a Viewsonic that likes a 1440x900 resolution, plugged it in and hey! There was the desktop. I was able to set it to the correct resolution, and all was happy. I then tried a further experiment; switching to 1024x768 while using the ATI driver, the resolution that I managed to get my own monitor to work on using the default open source driver. I then unplugged the work monitor, plugged in mine, and I was still OK.

So then for the final step. I went back to "Monitors", switched to 1280x1024, and as I type, my monitor is as happy as can be, even after a couple of reboots.

I'm not much of a techie, so I can't offer any explanations. But hopefully my info might trigger a few light bulbs in more competent heads and end up helping somebody else.

Thanks for your help, Temujin.

---

