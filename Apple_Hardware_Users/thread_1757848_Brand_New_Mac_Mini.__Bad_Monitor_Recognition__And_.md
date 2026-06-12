---
title: "Brand New Mac Mini.  Bad Monitor Recognition?  And No Unity?"
date: 2011-05-13
forum: Apple Hardware Users
---

### Post by MegaLoler on 2011-05-13
So I bought a new mac mini a little over a week ago.  I just now got  around to installing Ubuntu on it, which I had planned to do.  The first  thing I noticed was that when I tried to load it from grub the screen  displays noise and it hangs.  I got around this by adding "nomodeset" to  the grub command.  I say this in case it has something to do with my  current problem.

Now I am in Ubuntu but the next thing I noticed is  that it says that I don't have the hardware for running Unity.  That  can't be because it is brand new.
The next thing is that it only  detects one of my two monitors plugged in (via digital not analog) and not even at the correct resolution.  It is labeled "Unknown" in the monitors preferences, and the available resolutions only go up to 1024x768.

I want to be able to use both of my monitors at their native resolutions the way I can in Mac OS X (they were perfectly fine in Mac OS X).  Then I want to be able to use Unity.  Does "nomodeset" have anything to do with it?  I don't know what that does.

Thanks for any help.

EDIT:  While trying to get minecraft to run I stumbled upon the solution.  System -> Administration -> Additional Drivers  and enable the ATI/Nvidia drivers.  This fixed Unity and the resolution problem.  However I still don't get my second display.

---

