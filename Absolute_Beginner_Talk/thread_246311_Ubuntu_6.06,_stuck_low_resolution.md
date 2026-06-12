---
title: "Ubuntu 6.06, stuck low resolution"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-08-29
I got that XServer error, and tried a reinstall before I noticed the fix here on the forums. 

So, I stuck in a voodoo3 card and some extra RAM I had laying around, and I ran into some problems.

My Voodoo3 card has always run just fine on a 1024x768 setting with Ubuntu Breezy when I had it in, and before the reinstall it was perfect at 1280x???.  Does anyone know how to get my resolution back up again, to 1024x768? The option isn't there in the Screen resolutions settings. I click to dropdown the menu, and 640x480.

What do I need to do to enable? I've installed twice on that card tonight, so a reinstall probably won't do it.



Edit: Nevermind. I just had to play with the configuration more. I typed sudo dpkg-reconfigure xserver-xorg twenty or so times 'till I got it right.

Why is that configuration always so touchy? Even when I put the correct info in.

---

### Post by moore.bryan on 2006-08-29
*i ran into some of the same problems.  linux's double-edged sword is its customizability; meaning, everyone's machine is different and linux can't really predict everyone's setup.  i'm glad you stuck with it, though.*

---

### Post by jorn on 2006-08-29
There are lots of posts concerning that issue. Do a search in this forum.
> sudo dpkg-reconfigure xserver-xorg
will lead you to a setup where you can choose resolutions.
Another method is to add resolutions at the end of the file:
/etc/X11/xorg.conf
Before editing your /etc/X11/xorg.conf file make a backup:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

