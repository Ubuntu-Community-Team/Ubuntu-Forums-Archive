---
title: "Too Many Monitors"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by lledurt on 2007-04-24
I am still new to ubuntu but I am getting there.  

I had 2 monitors working great using the nvidia twinview option. I acquired a 3rd monitor and decided to give it a try. I purchased an identical video card to the first one (GeForce 7600 GT OC) and tried to link the two devices using Xinerama.  I have been reading the ubuntu hacks book. I am really not that smart.

Here is the problem I am having.

With 2 monitors both monitors were separate (the panels did not stream across them and the login was not half on on and half on the other) but I could scroll across both.  When I maximized something it filled only one monitor.

With 3 monitors the 2 connected to the same video card act as one.  Since it is device 0 the login and everthing is split.  The third works great when maximizing etc.

I copied the device 0 in the xorg.conf file exactly and made one 0 and the other 1.  Then split them like the hack said in ServerLayout.

**The other problem I have is that I can no longer run a terminal**.  Everything else seems to work fine.

Let me know if you need my xorg config

The only thing I did strange was I left the twinview option true on the second device even though there is only one monitor.  I think this is not my problem because when after I set up my 2 monitors I unplugged one and it auto-recognized on boot and ran like only one was configured.

Thanks P.J.

---

### Post by Happy_Man on 2007-04-24
Hmm... your xorg.conf would be nice...

---

### Post by lledurt on 2007-04-24
O.K. 
I attached my xorg.config for my setup using twinview and Xinerama setup(xorg.txt file).  There are 2 monitors connected to device 0 and 1 monitor connected to device 1.  This gives me 3 working monitors with the monitors on device 0 blending together and having windows span across unlike the normal twinview setup.  The third monitor works great.  My gnome-terminal does not open with this config.  everything else does.  It says starting terminal but then gives up.  I can not find anything in a log file about it failing.  
   I have also tried not using twinview and separating the monitors into 3 screens and using Xinerama.  This works for the first two monitors, but I get nothing but a black screen for the third.  I am guessing Xinerama only supports 2 screens?  I will research that.  Also the terminal does not work in that either.  Is terminal not compatible with Xinerama?  The other attachment (xorgxin.txt) is the xorg file for this try.

P.J.

---

### Post by lledurt on 2007-04-24
Partial Success

I fixed a mistake in my xorg.conf file that I was experimenting with.  It works as desired if I do not use twinview and just have 3 devices using Xinerama and split the video cards into screens 0 and 1.  I guess it does support more than 2.  The second card also had to name the screens 0 and 1.  
The good news is that all three monitors act as desired.  when maximizing something it fills the monitor only not any other monitor.

My problem is that gnome-terminal still won't run.  Is that a Xinerama issue?  I have a feeling it is having trouble finding the proper location for the window on the screen.  Any thoughts?
P.J.

---

