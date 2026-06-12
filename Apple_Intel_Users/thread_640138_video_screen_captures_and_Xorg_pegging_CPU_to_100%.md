---
title: "video screen captures and Xorg pegging CPU to 100%"
date: 2007-12-13
forum: Apple Intel Users
---

### Post by Abacaxi1979 on 2007-12-13
Hello all...

I'm running Gutsy Gibbon on a 15" Macbook Pro C2D w/ ATI Mobility Radeon X1600 and have been trying to take some video screen captures for a custom demo of Compiz Fusion for work.  Compiz Fusion works great so it seems I have full video acceleration.  Unfortunately when I begin taking a screen capture using Xvidcap, Recordmydesktop, or Istanbul the whole system slows down to being barely usable.  When I stop the capture everything returns to normal.  The result is a capture of a really sluggish desktop...very unexciting for a demo!  :) 

At first I suspected on-the-fly encoding during the screen capture, but running 'top' while  attempting a screen capture indicates that Xorg is what's pegging the CPU to 100%.  When I stop the capture Xorg's CPU utilization goes back to normal.  Also, disabling the desktop effects makes no difference in the behavior, nor does lowering the screen resolution.  Any ideas?

Thanks!

- Dan

---

### Post by Abacaxi1979 on 2007-12-16
Just out of curiosity, has anyone else with a MBP w/ ATI video card been able to use recordmydesktop without an issue?  Could someone with this configuration try it and let me know if they run into the same?

While looking for other similar reports, I found that they weren't necessarily isolated to MBP's with an ATI video card (well, okay, judging from lack of response to my posting maybe it is just me!  hehe), but there were similar reports of the same issue on other forums regarding PC desktops and laptops with ATI video cards, as well.  Either way, I could find no response to these reports (e.g. [http://www.phoronix.com/forums/showthread.php?t=3817](http://www.phoronix.com/forums/showthread.php?t=3817)) or they resigned to simply using a video camera.      

I managed to find an acceptable workaround, though.  To give some background on my setup, I used the recipe on this forum to install Gutsy Gibbon on my MBP, which included references to manually installing the official ATI video drivers and what modifications need to be made to the Xorg configuration.  This was from about a month ago and Compiz Fusion worked great.  Since then there have been some updates to the ATI linux drivers.  I tried installing the updated drivers yesterday, and while it seems that Compiz Fusion effects seem more snappy with the updated drivers, the problem with video capture persisted...bah.

I searched some more and came across what claimed to be a simpler way to get Compiz Fusion working with ATI video cards:  install xserver-xgl rather than dealing with too much editing of xorg.conf.  I figured I'd give that a shot and installed xserver-xgl from apt-get, restarted my X server which started xgl.   The desktop effects were still working but doesn't seem as snappy as with xorg (maybe just a perception thing).  I tried a screen capture with recordmydesktop, and while the xgl process started to spike in CPU usage (xorg remained nominal), the system remained responsive enough for applications to continue running decently during the capture.  Yay...mission accomplished.

The only bad side-effect I've seen of using xgl is OpenGL screensavers such as Flurry look like crap, and running glxgears just crashed the system.  I'm not too worried about OpenGL since this is only a temporary workaround just to get the screen capture, and I can just go back to Xorg after this is all done.  I got what I need out of this and don't feel like chasing dragons anymore, so if someone has a solution to OpenGL in xgl I'd be curious to know the fix for mine and others' information.  :)

- Dan

---

