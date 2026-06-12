---
title: "scale video output to display right on sony hdtv"
date: 2008-09-18
forum: Apple Hardware Users
---

### Post by cbl016 on 2008-09-18
Last Thursday I decided to take my old ppc g5 mac and install ubuntu on it and use it as a media center. So far everything has been working good. When I hook it up to my tv the picture looks great. However the current video driver doesn't scale the picture down to fit on the screen. The menu buttons on the top and the bottom cannot even be seen. 

I tried to install new video drivers but come to find out nvidia doesn't support power pcs. I then tried to install [nouveau]("http://nouveau.freedesktop.org/wiki/FrontPage") but I keep on getting the following error.

```
Build-Depends dependency for xserver-xorg-video-nouveau cannot be satisfied because no available versions of package libdrm-dev can satisfy version requirements

```

This thread shows how to change video mode on a ps3

[http://ubuntuforums.org/showthread.php?t=463274]("http://ubuntuforums.org/showthread.php?t=463274")

Is something like this possible for ubuntu 8.04?

Or is there another work around for this problem that anyone knows of?

Any help is appreciated. Thanks.

---

### Post by cyberdork33 on 2008-09-18
I think the problem that you are running into is that normally, TVs do not show the whole picture. There is a part that is overscan and you have to adjust the way the output is displayed in order to get everything you want viewable on the TV. ([http://en.wikipedia.org/wiki/Overscan](http://en.wikipedia.org/wiki/Overscan))

I am not all that familiar with all this, but there seems to be some information here:
[http://ubuntuforums.org/showthread.php?t=660213](http://ubuntuforums.org/showthread.php?t=660213)

---

