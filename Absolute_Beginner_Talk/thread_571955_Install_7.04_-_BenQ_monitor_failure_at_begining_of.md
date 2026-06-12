---
title: "Install 7.04 - BenQ monitor failure at begining of set up. New user"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by matheuu on 2007-10-09
Hello

I  have a friend willing to try Ubuntu, I have been using it for a while but not an expert.
We have finally got a cd burnt and made the computer boot from dvd not hard drive. 
The computer has xp on it and we want to keep it.

What happens is that when we try install,  is that the loading bar comes up, then the screen comes up blank with "OUT OF RANGE" then the ubuntu start up sound happens, then the dvd drive stops.

Please help if you can.
Don't want another person lost.


Mat

---

### Post by molly_001 on 2007-10-10
Mat,

Your X Window Manager needs to be reconfigured.

If you continue to boot from the Live CD (or even if you install), when the screen goes blank do this:
    (1)   Hit simultaneously:   CTRL + ALT + F1
    (2)   Login if asked
    (3)   type:
               sudo dpkg-reconfigure xserver-xorg

You will then be prompted through several blue screens to make specific choices about how to configure Ubuntu to work with your graphics adapter.

Now, you should reply back in this thread what graphics adapter or graphics card your friend has.  If you have no idea, a good starting point is to post the model number of the computer if available.  It's the not the Ben-Q monitor, but rather the xorg.conf file needs to be reconfigured.  That file tells Ubuntu how to communicate to the graphical subsystem, among other things.

If you want a heads up on what to expect when you execute sudo dpkg-reconfigure xserver-xorg, start looking at step #11 here:
[http://www.mepisguides.com/Mepis-6/nvidia-glx/dpkg-reconfigure/nvidia-dpkg.html](http://www.mepisguides.com/Mepis-6/nvidia-glx/dpkg-reconfigure/nvidia-dpkg.html)

---

