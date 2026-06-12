---
title: "Failure to resume in Jaunty on MacBookPro4,1"
date: 2009-08-28
forum: Apple Hardware Users
---

### Post by ianclarke on 2009-08-28
I've been very pleasantly surprised by how well Ubuntu works on my MacBook, but the one fly in the ointment is that I can't persuade my MacBook to wake up from a suspend.  I basically have to power it down and reboot.

It suspends just fine, pulsating front light and everything, but when I try to wake it up (by briefly pushing the power button) all I get is a black screen with a blinking cursor in the top-left corner.  There is no noticeable hard disk activity, and nothing other than powering down seems to have any effect on it while in this state.

I've tried every tip I could find but none improved the situation, the result of this is the following /etc/default/acpi-support file:  [http://gist.github.com/177201](http://gist.github.com/177201)

Looking at the pm-suspend.log file, it doesn't look like its having any problems suspending, just waking up again: [http://gist.github.com/177212](http://gist.github.com/177212)

What else?  Oh, I installed the NVIDIA accelerated graphics driver (version 180) through the Hardware Drivers Administration dialog, and it is activated and in use.

Any help would be greatly appreciated, if I can resolve this I'll be able to wave goodbye to OSX for good!

---

### Post by amd-64 on 2009-08-29
If you add the following to /etc/apt/sources.list
```
 
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main

```

You may be able to use nVidia 185 or 190. I am using 185 and it works well. 

You changed a number of options in acpi-support. Right now, resuming does not write anything to pm-suspend. Reinstall acpi-support and only add the sky2 unloading (or unload it manually) and see if resuming goes any further than this.

---

### Post by ianclarke on 2009-08-29
Many thanks for your efforts to help.

I've installed Nvidia 190 and it appears to be up and running.

I also did an apt-get purge and re-install of acpi-support, which I believe should have reset the config files.

The only change I then made to acpi-support was this line:

MODULES="sky2"

Regrettably these changes did not improve the situation :-(  The system suspends just fine, but when I try to wake it up all I see is a black screen with a blinking cursor in the top-left corner :-(

Do you have any other suggestions about how to proceed?

---

### Post by ianclarke on 2009-08-31
Just wanted to ping this thread to see if anyone can help me with this, since I still haven't found a resolution to this issue.

Many thanks,

Ian.

---

