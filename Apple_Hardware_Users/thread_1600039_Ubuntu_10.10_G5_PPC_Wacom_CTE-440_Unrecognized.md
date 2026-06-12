---
title: "Ubuntu 10.10 G5 PPC Wacom CTE-440 Unrecognized"
date: 2010-10-18
forum: Apple Hardware Users
---

### Post by cicada1 on 2010-10-18
I am having problems with my Wacom tablet using a G5 PPC running Ubuntu 10.10, is there anyone else having a similar issue? I found a solution here.

[http://askubuntu.com/questions/11815/how-to-install-wacom-bamboo-pen](http://askubuntu.com/questions/11815/how-to-install-wacom-bamboo-pen)
[https://launchpad.net/~doctormo/+archive/wacom-plus]("https://launchpad.net/%7Edoctormo/+archive/wacom-plus")

Add the PPA to the other software tab in your update manager then reinstall xserver-xorg-input-wacom and then reinstalled wacom-dkms. Gimp, Inkscape, and MyPaint work well. In Synfig make sure to select stylus and window to be in pen mode,
and have the drawing icons line up with your grid. Many thanks for this PPA.

---

