---
title: "Audio and Wacom issues"
date: 2009-08-22
forum: Apple Hardware Users
---

### Post by aermartin on 2009-08-22
When I installed ubuntu , I encountered 2 issues.

* my internal speakers are the only ones working, I have some external plugged in but i cant get sound out of 'em :/ anyone know why? when I google the issues people seem to have it the otherway around.

* my wacom only works if I unplug and plug it in again. I've tried to fix it by manually editing the xorg.conf only resulting in a faulty xserver startup, - falling back on my xorg.conf backup

Im very thankful for answers.

Im currently trying to install XSI , I even got the lictools to start now, seem I missed some i386 dependencies or something. wish me good luck!

---

### Post by Favux on 2009-08-22
Hi aermartin,

Welcome to Ubuntu Forums!

Some more information would help others help you.

For example which version of Ubuntu did you install?  Jaunty (9.04)?  Which Mac do you have?

To identify your sound card enter in a terminal:
```
aplay -l
```

Which Wacom tablet are you using?  If you are using Jaunty you are "suppose" to configure Wacom through the 10-wacom.fdi not xorg.conf.

---

### Post by aermartin on 2009-08-23
Hey favux and thanks! Ubuntu is actually working so good, I might remove my dualboot. But Im gonna wait with that.

Im actually not new to linux, once I used slackware , then gentoo. And now I'm back for ubuntu and Im amazed at all the grahpical interfaces for package management. I managed to install XSI , I just used the synaptic package handler and downloaded some i386 dependencies libs and now it works.

but the wacom issues remains, as soon as I reboot . i have to unplug, then replug the wacom to make it work.

It's a regular intous3 , the most common series. Okay So I read about the 10-wacom.fdi but I didn't really see any settings to make it turn on when X server starts. :/ but there gotta be some hotplug settings to switch so it's on by default.

the sound issues remains also, I've not had the time to resolve it. Just the interal speaker works, and it seems to be some problem with the switch that should turn internal off and external on when a plug is present. By the way my Mac is an iMac aluminium 2008 so the jack for external speakers I use is the headphone jack. 

This is what aplay -l , lists for hardware.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Favux on 2009-08-23
Hi aermartin,

Well for sound try post 2 here:  [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)  It looks like you need to add 'macpro' to get MacPro support.  Just remember in Jaunty 'alsa-base' is renamed to 'alsa-base.conf'.

To set up your tablet see post #271 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=28](http://ubuntuforums.org/showthread.php?t=967147&page=28)  That's me answering the Intuos3 user on the previous page.

As for having to unplug and replug, I don't know.  You wouldn't configure hot plugging in the 10-wacom.fdi.  If it's in a.fdi that should be configured in an upstream .fdi.  Maybe you need a specific "quirk" added upstream in your laptop specific .fdi.  I don't know if there is one for the Mac.  It almost sounds like the wrong module (ie not wacom.ko) is grabbing the usb HID for your tablet and not releasing it until you replug.  I suppose that could involve a symlink in udev also.  I don't think other Intuos3 owners are reporting this.  You could try adding 'wacom' to the end of your "/etc/modules" to try and ensure wacom.ko is active at boot and see if that helps.

---

### Post by aermartin on 2009-08-23
The wacom is resolved, it was just a wake-up thing. since the driver worked just fine when I re-plugged it , I did this ...

added in /etc/pm/config.d/00sleep_module
SUSPEND_MODULES="wacom"

and now it works.

---

