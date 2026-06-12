---
title: "nvidia driver install -&gt; GLX goes away?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by gnoel on 2007-03-25
After having researched this forum extensively and found two opinions on nvidia ("use the version from synaptic" / "don't use synaptic - get it directly from nvidia") I decided to manually install from nvidia.com:

Version 1.0-7184
Graphics chip NV20 (GeForce3)

I had to install the Xorg SDK development package first, then ran the nvidia installer to success.  After backing up xorg.conf, I made the changes recommended in the nvidia readme doc (changed driver from nv to nvidia, verified 'Load "glx"' in the Module section, and removed 'Load "dri"'.

The following resulted:
- Nvidia splash screen briefly displayed when restarting X
- Screen aspect slightly stretched horizontally (adjusted monitor accordingly)
- GL support disappeared

For example, Google Earth previously had the annoying "Open GL" emulation, now it said it couldn't detect a video driver and came up blank.  Plus, all the screensavers were blank.  All 2-D stuff seemed unaffected (xearth wallpaper and desktop apps were fine).

Then I started thrashing around:

- loaded some stuff from the repository (currently Synaptic shows nvidia-glx 1.0.8776... and nvidia-kernal-common are installed)
- I added, then removed "glx" from some kernal module startup file (forgot to write that down)
- disabled "nv" in the linux-restricted-modules-common file, then removed the reference
- ran 'sudo nvidia-xconfig' to tweak the xconfig file.

Nothing had any effect.  Hoping for a "do-over", I uninstalled the nvidia driver using the nvidia installer and reset xorg.config to what it was before this whole sorry mess started.  Now, I have lots of xconfig files and I'm back to using the nv driver, except that GL is still not working.

](*,) 

I'm looking for advice on where to go from here.  Thanks in advance!

---

### Post by r4ik on 2007-03-25
Sorry.

---

### Post by gnoel on 2007-03-25
I tried Alberto's Envy thing anyway (as previously advised by r4ik before a change of mind) and it didn't work.  I couldn't restart X so I went into terminal mode and restored xconfig.  nvidia-glx-dev is now a "broken package" (according to synaptic) but I'm still apparently up on nv, but I no longer know what I have or don't have.  At least I still have one unshot foot left ...

Any ideas for a do-over?

---

### Post by r4ik on 2007-03-25
Synaptic - edit -fix broken package.
Sorry about you're foot.

---

### Post by gnoel on 2007-03-26
I finally figured out the solution to my problem.  I uninstalled the nvidia driver and rebuilt it from the file I downloaded from Nvidia.  That got me back to where the Nvidia driver was loaded but GLX was disabled.  Opening the Nvidia Xserver Settings GUI, I noticed the following error in the OpenGL/GLX tab:

"The OpenGL extension 'GLX' is not supported by the X server or there was a problem retrieving GLX information from the X server."

So I googled this error and "got lucky" here: [http://www.nvnews.net/vbulletin/showthread.php?t=67150](http://www.nvnews.net/vbulletin/showthread.php?t=67150), where I learned that there might be a conflict with the Composite extension.  So I added the following to my xorg.config:

> Section "Extensions"
    Option         "Composite" "Disable"
EndSection

Google Earth is happy, I am happy.  Off to race a penguin! :-)

---

### Post by wulfhound on 2007-03-29
> **gnoel said:**
> I finally figured out the solution to my problem.  I uninstalled the nvidia driver and rebuilt it from the file I downloaded from Nvidia.  That got me back to where the Nvidia driver was loaded but GLX was disabled.  Opening the Nvidia Xserver Settings GUI, I noticed the following error in the OpenGL/GLX tab:

"The OpenGL extension 'GLX' is not supported by the X server or there was a problem retrieving GLX information from the X server."

So I googled this error and "got lucky" here: [http://www.nvnews.net/vbulletin/showthread.php?t=67150](http://www.nvnews.net/vbulletin/showthread.php?t=67150), where I learned that there might be a conflict with the Composite extension.  So I added the following to my xorg.config:


Google Earth is happy, I am happy.  Off to race a penguin! :-)

THANK YOU THANK YOU THANK YOU! I killed the mobo on my VIA Pentium ATI POS.....something to do with windows dual booting.....actually it had been going for along time, and I believe that it was better off, right....so I would be forced to get a different setup (NVIDIA).

Well, after freecycling someone gave me a computer that had an Nvidia 2100+ CPU. The graphics processor (I have no video card) is a GeForce4 MX Integrated GPU. I decided to intall the Nvidia legacy drivers, the same way you did...I had to install various things but thankfully the Nvidia installer is very nice in telling you exactly what you need. So, I did it...but then I had the same problem as you, where GLX was just...gone.

Thanks to your post I am hopefully all set!

Thanks,

Sandaili

---

### Post by bob365 on 2007-09-23
I know this will be really random but, how do you get those cool pictures by your name?

---

