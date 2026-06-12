---
title: "everything became larger..."
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by holdie on 2007-01-13
hey everybody...this is my first post but i've been lurking for a while now, anyways here's my problem...

I recently decided to take the plunge and attempt to install compiz with aiglx...i just installed the compiz files with synaptic, then followed an online guide to go through the terminal:

[http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

I followed the instructions the first time but missed one small step in editing the xorg file, inadvertently crashing my graphics card...

anyways, I booted in safe mode, took at the manual for the xorg which told me to input this line of code:

sudo dpkg-reconfigure -phigh xserver-xorg

I did that, updated, and everything now runs smoothly except that now everything is significantly larger...the screen resolution is the same, however the toolbar, icons, windows, etc appear as though I was operating at a much smaller size...any ideas as to what's going on???

oh, and on a side note, i fixed the problem with xorg.conf and got compiz to boot, but it seems to be very buggy and very unstable, is there a better way to go about installing?

thanks

---

### Post by BarfBag on 2007-01-13
Did you make a back-up of your original XORG config file?  Does it say it's on one resolution, but looks like it's on another?

Compiz is buggy.  Since it isn't being maintained (as Compiz), I suggest going with [Beryl]("http://www.beryl-project.org/").  It runs very smooth and is fairly stable.  Here's [ nVidia]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29") and [ATI]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29") instructions.

---

### Post by holdie on 2007-01-13
unfortunately no...that was pretty retarded I know, that's why I was trying to just get the latest version of the file (which i think i did) since I had to edit everything all over again.

and yeah, what you're describing is pretty much it...the resolution says it's on the highest setting, but everything appears large and fuzzy as though it were on one of the lowest...

---

