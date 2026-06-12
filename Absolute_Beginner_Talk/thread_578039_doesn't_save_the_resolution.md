---
title: "doesn't save the resolution"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-16
My nvidia driver won't save my resolution after a restart.  When Ubuntu is running I can change the resolution just fine, but when I restart it's back to the lesser resolution

---

### Post by milton1 on 2007-10-16
two possibilities:

1) make sure you are running nvidia-settings with root permissions (assuming you are running nvidia-settings at all)

2) Add this to the "screen" section of your xorg.conf file

```
Option "DynamicTwinView" "False"
```

---

### Post by sayuki288 on 2007-10-16
sudo nvidia-settings

---

### Post by keeskuip on 2007-10-21
Same problem here.

I can set the right resolution with nvidia-settings.

But when I restart X it will go back to the 1024 resolution.
Can't seem to get this to work. Is this something with failsave
x startup?

Kees.

---

### Post by omrsafetyo on 2007-10-24
running nvidia-settings in root doesn't help at all - at least not in all cases.

nvidia-settings.rc does not hold the resolution configurations for the program.  Does anyone know where these settings are loaded from when it starts up?

---

### Post by diddler on 2008-01-27
Same problem and no one seems to have a solution, but that doesn't surprise me.

I have recently added an Acer 22" Widescreen to my setup.  I have a NVIDIA 6800XT and have the proprietary drivers installed (although, admittedly, not the latest version).  The proprietary driver is active. 

 I go into System Tools/Sysinfo/Nvidia/Nvidia Display Settings/Xserver display settings and I am able to set the resolution to the 1680 x 1050 that is native to the monitor.  The settings load and the display is perfect.  The new monitor shows up in all the dialogs as well.

I then punch the "Save to Xconfiguration file" and, theoretically, save the settings.

Here is the problem:  Whenever I turn the computer on it reverts back to the 1024 x 768 setting it had for my old LCD monitor.  I even tried checking the "Force Full GPU scaling" box to see if that would force the system to load the native resolution for the new monitor.  It didn't.

Unlike many of the other problems here, I can get the desired resolution and the video seems to work just fine, BUT, I have to manually reset the resolution each time I boot up.

Any suggestions on how to get the $#@%^ system to remember the desired resolution?

---

### Post by diddler on 2008-01-31
OK.  I solved my problem.

Here is how I did it:

I followed someone else's advice posted in another thread on how to edit xorg.conf.  

This resulted in my Nvidia proprietary drivers being totally disabled and everything being set to generic monitor and generic video card (and still the wrong resolution).

I went back in to the system/administrator menu and clicked to re-enable the restricted driver.

This caused Ubuntu to remove the existing restricted driver and download the newer nvidia restricted drivers (a 45 minute process due to my dial-up connection).

The newly installed drivers required a re-boot, which I did and when the screen came back up, lo and behold, it was the desired (native) resolution of my new monitor.

Now I realise that the Nvidia system menu will not ACTUALLY save changes so fortunately I am at the resolution I want.

My advice for Nvidia users with new monitors is this:  remove the restricted drivers, reinstall the restricted driver, re-boot and see if it defaults to the resolution that you want with your new monitor!  Worked for me at least, certainly better than editing the config file did!

---

