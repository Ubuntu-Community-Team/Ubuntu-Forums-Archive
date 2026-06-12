---
title: "nvidia driver problem (compiz problem?)"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ubunoobie on 2007-10-26
I'm not sure exactly how to best describe the problem I am having, but here goes:

I installed 7.10 with no problems. Now when I boot up and come to the desktop, I am reverted back to a basic (native resolution?) desktop... I'm assuming this is because my video card is not "found" upon bootup. Well then I went into System > Administration > Screens and Graphics and I clicked on "Driver," found the driver for my card (GeForce 8400GS) and applied the correct driver for my card (the "nv" driver). Then a dialog told me to log out for changes to take effect (I'm guessing to restart x), which I did, and voila, I have a high resolution desktop upon logging back in. No problems so far.

Now that I have the video card working I proceed to try to turn on the fancy desktop effects (compiz?) under System > Preferences > Appearance ("Visual Effects" tab) and I click on "Extra" which gives me a dialog box that says to please restart computer and run "Appearance/Desktop Effects" again after restart. This is where the problems begin.

I restarted and the first thing that went wrong was that I got reverted back into low graphics mode again! What happened? Did the video driver settings not "stick" (the ones I manually set)? It's like by restarting, the whole system was somehow reset. So when I came back to the login screen and then desktop, I was back to low resolution. I can't even deal with the desktop effects yet, because my video card is not being utilized to begin with.

So I went back into "Screens and Graphics" and noticed that the video card driver had in fact been reset! As if I never made a change to it! So then I changed it again, and logged out for the changes to take effect, ect ect. And repeated the process described above.

I've done this 4 times now with the same results.

:confused:

---

### Post by nick_h on 2007-10-26
For the visual effects you will need the restricted driver "nvidia" rather than the open source driver "nv".  Try installing the driver from System > Administration > Restricted Drivers Manager.

---

### Post by ubunoobie on 2007-10-26
> **nick_h said:**
> For the visual effects you will need the restricted driver "nvidia" rather than the open source driver "nv".  Try installing the driver from System > Administration > Restricted Drivers Manager.

Ok, thanks! You know what I just realized, to get a higher resolution, just simply fix that under "Screens and Graphics." Let me restart now just to make sure this doesn't change on me again.

---

### Post by fahadrather on 2008-01-13
thanx...now i can change my screen resolution....earlier,the low screen resolution created certain problems...but still after restart, the resolution changes by itself....why???...and how to sort it out

---

