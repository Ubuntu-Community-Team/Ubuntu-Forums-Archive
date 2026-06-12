---
title: "screen resolution messed up"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by mezerik on 2008-05-28
My screen resolution should be 1680x1050 on my 4th generation mbp.
Everything was working fine until one startup when i got an error to do with the graphics board or something similar.

Now it's stuck on 640x480

I have checked the file /etc/usplash.conf and the parameters are set correctly to 1680x1050

In OSX everything is fine, there is no problem with the graphics or resolution, so i assume it's a setting in ubuntu that needs tweaking.

Any help much appreciated.

---

### Post by cyberdork33 on 2008-05-28
There was a kernel update a few days ago, and if you were not using the proprietary driver from the repos, that would break it. How did you install the driver?

---

### Post by mezerik on 2008-05-28
seems i fixed it by reverting xorg.conf to it's original state.

All i had done in there was change the trackpad configuration, seems it messed up the graphics somehow.  All is working fine now, although i would like to know how i right click using a mbp in ubuntu

ctrl click doesn't work

I usually use two fingers and click in osx

Also i would like to use the two finger scroll that is available in osx, is it possible.  The bug fix i used before didn't work and was what messed up the graphics i think.

---

### Post by cyberdork33 on 2008-05-28
> **mezerik said:**
> seems i fixed it by reverting xorg.conf to it's original state.

All i had done in there was change the trackpad configuration, seems it messed up the graphics somehow.  All is working fine now, although i would like to know how i right click using a mbp in ubuntu

ctrl click doesn't work

I usually use two fingers and click in osx

Also i would like to use the two finger scroll that is available in osx, is it possible.  The bug fix i used before didn't work and was what messed up the graphics i think.ctrl click won't work either unless someone writes a daemon or modifies some existing drivers/applications.

two-finger tapping can be enabled in the xorg.conf. two-fingers-on-pad+click can be enabled with the modified version of the synaptics driver that volanin created.

You should not just copy and paste the entire configuration. You only need to use the options that you actually want. run 'man synaptics' and it will tell you about all the available options.

---

