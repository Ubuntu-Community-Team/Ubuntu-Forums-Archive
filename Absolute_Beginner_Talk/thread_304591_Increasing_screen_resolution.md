---
title: "Increasing screen resolution"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by bparkis on 2006-11-22
Hello.  I just installed Ubuntu and somehow my screen resolution is stuck at 640 x 480.  I tried using the menus, System->Preferences->Screen Resolution but 640 x 480 is the only option listed there.  I can get 1024x768 resolution from Windows.  What's the most likely fix?  Thanks

---

### Post by bparkis on 2006-11-22
Never mind, I installed the updates and rebooted and now I can access the higher resolution.

---

### Post by housam on 2006-11-22
I've tried this and it worked out.

[COLOR="Red"]Originally posted by confused57[/COLOR]

You might want to read how to reconfigure the xserver:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

Basically, what you'd do is open a terminal(Applications---Accessories---Terminal), enter:

Code:
> sudo dpkg-reconfigure xserver-xorgYou might want to select "No" at the first screen for automatically detecting your monitor, then select the defaults for everything else, except select the "nv" or "vesa" video driver...and place an (*) by the resolutions that you want to use. The link above explains all of this.

---

