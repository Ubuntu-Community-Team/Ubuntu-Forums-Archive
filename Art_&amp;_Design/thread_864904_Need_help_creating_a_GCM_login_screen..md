---
title: "Need help creating a GCM login screen."
date: 2008-07-20
forum: Art &amp; Design
---

### Post by jay019 on 2008-07-20
Hi all,

I have made a GDM login screen before, but I was wondering if anyone has any idea how I can make one similar to...

[http://download.tuxfamily.org/geubuntu/screens/screen04.jpg](http://download.tuxfamily.org/geubuntu/screens/screen04.jpg)

I just like the photo background with the login part raised and not sure what to do in gimp to get the same effect.

Any help or pointers appreciated.

Jay

---

### Post by paullinux on 2008-07-20
This GDM-theme was made with photoshop I believe.  But with Gimp you can go a long way:

Make a new (transparent) image a bit bigger then the login-screen you want to make.  Then apply a gradient on the picture from brown to white.

You then set the transparency to 50 % (or less if you prefer).  You then select the whole image. Go to the select-menu and choose rounded selection. It's default 'rounding' is set at 50 % which is fine I think. 

You then copy the rounded selection.  Make a new transparent image with the a slightly bigger size as the original one and paste the copied rounded selection on the image. 

To create a shadow: go to filters/light and shadow/drop shadow and apply this to your image. Play a bit with the settings to get the shadow you want.

You should then have a semi-transparent rounded gradient image to use as a basis for your GDM-theme. 

Be aware: A GDM theme has a center-image used for the actual login-screen and a background-image. There are thus two images to get the effect you want.

Note: You really should experiment with Gimp. 

Good luck !

---

