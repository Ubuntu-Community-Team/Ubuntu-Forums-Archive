---
title: "Can't change video resolution"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by DSundquist on 2006-10-21
I've just loaded Kubuntu on a 6~7 year old Gateway with banshee voodoo graphics card and I believe 16M of video memory.  The install went fine but I can not change the resolution off of 640X480 (as administrator).  At 640x480 most windows are too large for the screen and I can not get to apply, continue, and cancel buttons.  Obviously this is severely hampering my experience.  Any assistance would be appreciated.
Thanks,
Doug

---

### Post by caravel on 2006-10-21
did you do: sudo apt-get install xserver-xorg-driver-tdfx    ?

Then: sudo dpkg-reconfigure xserver-xorg

Make sure you select the tdfx driver.

-Edit: Remember the Banshee is similar to a Voodoo1/2/3 in that it only supports 16 bit colour not 24/32.

---

### Post by Engnome on 2006-10-21
Try running ```
sudo dpkg-reconfigure xserver-xorg
```

in terminal.

Press enter about 20 times to get to the resolution part. Add the resolution you desire. Restart X. (reboot or ctrl + alt + backspace)

*Hopefully* that will do it. I must say I much prefer windows way of just trying a new resolution without all this rubbish.

---

### Post by DSundquist on 2006-10-21
Yeah I checked xorg.conf and did confirm tdfx is the driver. I noticed all of the resolution choices listed up through 1024 x 768 at each bit depth up to 16.  I'll give a try running the reconfigure.
Thanks
Doug

---

### Post by CatKiller on 2006-10-21
You may find it useful to find out the refresh rate ranges of your monitor - often people can only select 640x480 because the graphics card isn't reporting the rates properly, and they have to be added in manually.

---

### Post by DSundquist on 2006-10-24
Thanks, that fixed it.  I especially appreciate the tip on restarting X.

---

