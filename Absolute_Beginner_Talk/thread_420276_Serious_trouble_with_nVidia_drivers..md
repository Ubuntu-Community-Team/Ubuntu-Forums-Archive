---
title: "Serious trouble with nVidia drivers."
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-04-23
I've been having a lot of trouble setting up my nVidia driver on my current Feisty install, which is pretty strange, as I've never had problems with it before. 

First, I tried the restricted drivers manager, it installs fine, but the xserver crashes at the GDM. So I switch back to the nv driver in xorg, get back in, and I try Envy to install the drivers, which gives me no luck at all, either.

So, in Synaptic, I remove all the packages related to the nvidia driver, and start again with the Restricted Driver Manager. Same thing happens. 

I'm using a GeForce FX 5500, if that matters, and I'm using a 32 bit system. Normally I'd be satisfied with the NV driver, but my monitor's pretty dark even with the hardware brightness set to maximum, so i'd like to be able to adjust the settings in nvidia-settings.
 
Attached is the  /var/log/Xorg.0.log:

The part I believe to be relevant is 
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Is there perhaps a folder or some config files I could purge to get a clean attempt at installing this driver? Or any other options I might have?

---

### Post by sunexplodes on 2007-04-23
Any ideas at all?

---

### Post by igknighted on 2007-04-23
Try installing the kernel-headers package for the kernel you are running and install again.  The module wasn't built properly for some reason.  Then run Envy again, selecting manual install.  This should pull in the driver from nvidia.com and build the module to your kernel.  Note, even though it says manual it isn't really.

---

### Post by sunexplodes on 2007-04-23
Thanks, I'll try that. 

Just so I don't muck things up further though, what's the name of the kernel-headers package you're talking about? Is it the linux-headers package? 

Also, should I clear all of the currently installed nvidia packages first?

---

### Post by sunexplodes on 2007-04-23
Well, I tried this out, and no luck, same problem. Any other ideas? Or maybe I was trying with the wrong files?

---

### Post by sunexplodes on 2007-04-24
Any other suggestions?

---

### Post by slayerboy on 2007-04-24
I had an issue similar to this.  IIRC Envy isn't suited for Fiesty at all.

I can't remember what I did to get my system back up and running with the nvidia drivers, but try this as a start:

CTRL+ALT+F1 to a terminal screen, then login and type:
```
sudo killall gdm
sudo aptitude search nvidia
```Now when it lists packages with Nvidia in them, you might see some with "i"'s next to them on the left.  If there are, type this [COLOR=DarkRed](and only type the red if you don't have anything like wireless cards or anything else configured with the restricted manager)[/COLOR]:

```
sudo aptitude remove <REPLACE PACKAGE NAME HERE> <2ND PACKAGE NAME> <ETC, ETC, ETC>
[COLOR=Red]sudo aptitude remove envy linux-restricted-modules[/COLOR]
```Now change your xorg.conf to change to the NV driver and restart your system.

Now try installing the nvidia-glx-new package, [COLOR=DarkRed]nvidia-glx, or nvidia-glx-legacy depending on which one works, but try in order,[/COLOR] (IRC you can do this from add/remove programs) and then reboot.  If you don't see the Nvidia logo when X comes up, edit the xorg.conf and change the driver to Nvidia and it should work.

YMMV, as I said, this is the steps I believe I took to resolve my issues upgrading to Fiesty.  I know you tried this with synaptic, but it could have caused issues with X running.

Good Luck!

---

### Post by sunexplodes on 2007-04-24
I gave it a go, but sadly, no luck. Thank you anyway.


Anybody got any other ideas? This is so weird, I've never had any trouble with this!

---

### Post by slayerboy on 2007-04-24
ok...I kinda had that feeling that it might now work, but let's keep trying.   I have an idea...

Follow what I said in my post above, but notice the change I made in red and see if it works now.

---

### Post by sunexplodes on 2007-04-24
> **slayerboy said:**
> ok...I kinda had that feeling that it might now work, but let's keep trying.   I have an idea...

Follow what I said in my post above, but notice the change I made in red and see if it works now.

I'll give it a try, but meanwhile, on my most recent attempt, I noticed something odd in the log file: 
```
API Mismatch: The nVidia kernel module has the version 1.0-9755 but this X module has the version 1.0-9631
```

followed by the usual
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by slayerboy on 2007-04-24
> **sunexplodes said:**
>  I noticed something odd in the log file: 
```
API Mismatch: The nVidia kernel module has the version 1.0-9755 but this X module has the version 1.0-9631
```

Yeah, that's one of the issues I ran into and IIRC, uninstalling linux-restricted modules helped.  Then when you go back and reinstall the nvidia drivers it reinstalls that driver.  I think my problem was I was running Fiesty testing just when they implemented the nvidia-glx-new to get the "latest" drivers from Nvidia.  That's pretty much when it all started happening because it changed in the middle of me having problems with the Nvidia drivers to begin with LOL.

Not sure what's going on in your situation, but I have a feeling this might work ;):KS

---

### Post by sunexplodes on 2007-04-24
I'll give it another shot. I don't understand why this is happening. I've done a completely clean install today, and it is STILL happening.

---

### Post by sunexplodes on 2007-04-24
OKAY! Got it going with the original nvidia-glx driver. Don't know why it wasn't working before, but your instructions did the trick. Thanks for all your help!

---

### Post by Terl on 2007-04-24
Hurrah!  It works!

---

### Post by slayerboy on 2007-04-24
> **sunexplodes said:**
> OKAY! Got it going with the original nvidia-glx driver. Don't know why it wasn't working before, but your instructions did the trick. Thanks for all your help!

Glad it worked, and glad I could help :KS

If you could, please mark the topic as resolved.  It will help to serve as kind of a place that people will know they can at least look to see if they have the same problem and how it was resolved :)

---

### Post by sunexplodes on 2007-04-24
Consider it done.

---

### Post by tcdrewiv on 2007-04-25
Feedback: Your how- to fixed my API mismatch. Big Thanks! 

 The only snag I had was after restarting using the 'nv' driver the login screen was not visible but the audio drum role was present. I simply logged in blind and then the monitor came to life. After replacing "nv" with "nvidia" , restarting,changing resolution, everything works.. including beryl.

---

