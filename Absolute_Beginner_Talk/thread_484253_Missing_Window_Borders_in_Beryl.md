---
title: "Missing Window Borders in Beryl"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-25
Hi people.
It took me ages trying to get my ATI Restricted Driver to work correctly and ran Beryl with it in an XGL Session.

Anyway I was happy to see things work

 The following command gives me:
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition
OpenGL version string: 2.0.6473 (8.37.6)

So it looks like I got Direct 3D working.

And I installed Beryl with XGL and created an xgl.session after going though the tutorial on this link:

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

The only problem I see is that when I acctivate Beryl as the Windows Manager (with Emerald Themes), my windows do wobble and all, but I'm missing the windows borders. The Cube does not work either.

Anyone know how to fix this? It'll be greatly appreciated as it took me ages to get it to work the noob I am.

Thanks

---

### Post by ronocdh on 2007-06-25
Guide I used is in my sig, as is my chipset info. To solve the no window borders problem, you can change your windowing interface manager from Emerald to MetaCity. You won't be able to use your Emerald themes, but at least you can see the buttons! I had this problem on one of my various installations of Beryl, but I can use Emerald fine now. Odd, huh?

Are you by chance using 64-bit?

---

### Post by daimaru on 2007-06-25
well dont know an exact answer but try these two guides which are from the source:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

and this one. use method 2 installing manually
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by Rui Pais on 2007-06-25
hi,
some people seems to have that problem solved by edit /etc/X11/xorg.conf and add the line
```
 Option      "AddARGBGLXVisuals" "True"
```
at Section "Device" under the Driver line for your graphics card.

hth

---

### Post by ROUBOS on 2007-06-25
Yes Rui Pais I did that and did not work.

After looking through and reading on more people's advices to the same problem on this forum I found this:

[http://ubuntuforums.org/showthread.php?t=437802](http://ubuntuforums.org/showthread.php?t=437802)

Downloaded the mentioned file, did a chmod a+x on it in order to make it executable and copied it into /usr/bin

That made it work :D

I'm a very happy man now. :D

LOVE IT. LOVE THIS COMMUNITY

THANKS TO ALL I HAVE THE BEST OS RUNNING.

If only I could remember all these for the next time I install Ubuntu.

The link I just mentioned should be a Sticky as I've seen many people with the same problem as me.

Thanks to all again :D

---

### Post by swoll1980 on 2007-07-03
Just put a check in the windows decoration box

---

