---
title: "Problems with nVidia display"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by etothepi on 2008-03-04
Okay, I'm going to take the role of a whiny newbie here, and will ask for simple explanations - particularly if my problem is with kernels.  Pardon my indulgence.

I've just installed Ubuntu.  When I was booting off the CD, I played around with some graphics settings, and got it to recognize my nVidia 7600 card, and upped it to a usable resolution.

But now that I'm running it off a hard drive, it won't recognize anything.  It put me into low graphics mode (800x600).  I've attempted downloading the Linux drivers for my card, and chmod 755 the thing.  When I attempt to run it, nothing happens.  Just nothing.

From what I've read, it looks like I need to disable some prior nVidia kernel which is screwing everything up, but I don't know how to do that.  And maybe I'm supposed to do something else.

Help?

---

### Post by PmDematagoda on 2008-03-04
Open the Restricted Drivers Manager in System>Administration>Restricted Drivers Manager and then enable the Nvidia driver, see if that solves your problem.

---

### Post by uberlube on 2008-03-04
Use ENVY to install your graphics driver, its in the repositories. The live CD will use the restricted driver while its running but you have to install the actual drivers yourself.

---

### Post by etothepi on 2008-03-04
Aha!  Success!

Very odd - in the restricted drivers area, I had to deselect the nVidia, then *re*select it.  Upon reboot, success!

Thanks for the swift reply!

---

### Post by etothepi on 2008-03-10
I have recently installed Ubuntu, and had some issues getting the nVidia driver working properly.  I went to the Restricted Drivers and first disabled then re-enabled the nVidia driver which apparently installed the newest drivers.  Everything worked.

However, when I rebooted Ubuntu, everything has these weird patchy blocks everywhere, at odd angles.  I guess I'll check my current resolution to make sure my monitor can handle it (it should handle 1680 x 1050), but I wanted to check here too.

So, if I'm moving my mouse purely "up", on the display it moves to the right at "brick-like" intervals.

---

### Post by dcstar on 2008-03-10
> **etothepi said:**
> I have recently installed Ubuntu, and had some issues getting the nVidia driver working properly.  I went to the Restricted Drivers and first disabled then re-enabled the nVidia driver which apparently installed the newest drivers.  Everything worked.

However, when I rebooted Ubuntu, everything has these weird patchy blocks everywhere, at odd angles.  I guess I'll check my current resolution to make sure my monitor can handle it (it should handle 1680 x 1050), but I wanted to check here too.

So, if I'm moving my mouse purely "up", on the display it moves to the right at "brick-like" intervals.

You probably have a "Virtual" resolution higher than the actual physical resolution.

---

### Post by etothepi on 2008-03-10
By "virtual" I assume you mean the settings in System -> Preferences -> Screen Resolution  and "physical" you mean the resolution my monitor actually displays?

I fixed it (after some eye-exhausting trial-and-error finding the Screen Resolution menu), but the highest it will let me choose on Ubuntu is 1400x1050 for some reason.  My monitor's "best physical" resolution should be 1680x1050, but this is not a choice.

Both 1600x1200 and 1600x1024 mess up when I choose them.

Any advice?

---

### Post by Peter09 on 2008-03-10
Sarch the forums for details on how to modify your Xorg.conf file, you should put your required resolutions in there. 

Also it is worth downloading ENVY from here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

this will makes sure that the best NVIDIA driver is installed for you card.

PC

---

### Post by ad_267 on 2008-03-10
Try using the nvidia-settings manager to change resolution. I found that the usual ubuntu Screens and Graphics Preferences wouldn't set my monitor resolution properly. To do this enter "sudo nvidia-settings" into the console.

---

