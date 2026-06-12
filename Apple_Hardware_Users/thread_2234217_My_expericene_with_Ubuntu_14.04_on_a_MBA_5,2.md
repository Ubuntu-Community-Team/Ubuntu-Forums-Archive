---
title: "My expericene with Ubuntu 14.04 on a MBA 5,2"
date: 2014-07-13
forum: Apple Hardware Users
---

### Post by maestrobwh1 on 2014-07-13
I can say that I am fairly impressed with how well Ubuntu 14.04 runs on my generation of Air 5,2 (2013) right out of the box.

I have the wl driver installed for wifi over the open source driver.

I added this to /etc/default/grub before "quiet splash"

i915.i915_enable_rc6=1 intel_pstate=enable

The latter probably isn't needed, as I think it is the default cpu governor in 14.04.  Despite that it seems to lack functionality because there are only two available governors, it actually is just better from my experience because it doesn't "just" throttle the cpu frequency.

I also am using the mtrack driver for the touchpad and it is a WAY better experience than the default synaptics driver (post 6 is mine):

[http://ubuntuforums.org/showthread.php?t=2230690&p=13072306#post13072306](http://ubuntuforums.org/showthread.php?t=2230690&p=13072306#post13072306)

Lastly, I have a keyboard and display brightness daemon installed called lightum installed but the one in the repo seems only to work up to ubuntu 12.10 unless it is launched from terminal using -U.  The source has been changed and if built from there, the program works as designed on 14.04 with kernel 3.13.0.  I built a debian package from it and posted it here:

[https://dl.dropboxusercontent.com/u/48359498/lightum_2.3.1-ubuntu1_amd64.deb](https://dl.dropboxusercontent.com/u/48359498/lightum_2.3.1-ubuntu1_amd64.deb)

Then one can add the repo via these instructions to install lightum-indicator (frontend tray applet)
[http://ubuntuhandbook.org/index.php/2013/09/auto-adjust-keyboard-brightness-in-ubuntu-macbook-via-lightum/](http://ubuntuhandbook.org/index.php/2013/09/auto-adjust-keyboard-brightness-in-ubuntu-macbook-via-lightum/)

One could theoretically install that lightum package from the repo and just manually launch it from terminal before launching the tray applet using "lighum -U" which ignores some dbus error that would prevent it from starting, but I wanted the fixes the author has made.

---

