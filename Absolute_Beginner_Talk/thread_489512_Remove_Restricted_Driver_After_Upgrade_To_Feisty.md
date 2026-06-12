---
title: "Remove Restricted Driver After Upgrade To Feisty?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by linux4me on 2007-07-01
I just successfully upgraded from Edgy to Feisty using the Update Manager. Very nice!

The first time I logged on after reboot, the Restricted Drivers Manager opened, showing that I had two restricted drivers installed. One is the Nvidia accelerated graphics driver which shows as enabled and in use. The other, and the topic of this post, is:
> Lucent/Agere linmodem controller driver
which is disabled and not in use.

I have an internal Intel 536 modem which was working in Edgy. It wasn't working initially after the upgrade to Feisty (different kernel?) so I used the instructions in the Wiki to install the Feisty version of the driver, and it is working perfectly now. Apparently, that driver is supported, because no new entry appeared in Restricted Drivers Manager after I installed it. However, the old "disabled" and "not in use" Lucent driver above is still listed.

What I would like to do is completely remove the old driver and the entry in the Restricted Drivers Manager for it so it doesn't cause any confusion or problems down the line. 

I have looked at my /etc/X11/xorg.conf, and there is no entry for the modem in there. I checked my /etc/modules file, and there is only one entry for the Intel536 in it. I searched in Synaptic for the old driver, but couldn't find it. I searched the forums and couldn't find an answer, but it may be I'm not using the right search terms.

How do I remove the old driver and its entry in the Restricted Drivers Manager?

Thanks!

---

### Post by DBStevens on 2007-07-01
The synaptic search should be for the word restricted, the modules are in one of the linux-restricted packages.

They come as a group and can't be individually removed through synaptic, just toggled on/off through the restricted driver manager.

---

### Post by linux4me on 2007-07-01
Wow! I hit the jackpot searching Synaptic for linux-restricted. Thanks, DB.

Would it be safe to uninstall the linux-restricted-modules that have an earlier version number than my Feisty install (2.6.20-16-386 via uname -r) to see if that gets rid of the Lucent/Agere entry in Restricted Devices Manager since it is diabled and not in use? 

The only other entry I have in Restricted Devices Manager is my Nvidia drivers as noted above, but they shouldn't be in one of the linux-restricted-modules, should they?

---

### Post by DBStevens on 2007-07-01
I'm afraid that your nvidia driver is part and parcel of the restricted-drivers packe you will not be able to remove one without them all being removed.

Which was what I said in line two, now if you are feeling up to the task you could always play programmer with  the restricted driver manager.   I'm sure that a contribution of a properly functioning modified version of the program would be welcomed by the community.

---

