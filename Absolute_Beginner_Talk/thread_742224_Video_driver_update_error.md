---
title: "Video driver update error"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Will Walshe on 2008-04-01
Hi guys, I'm a linux newbie who has just migrated over from windows.

I'm running the ubuntu ultimate edition 1.4 distribution. I recently attempted to update my video drivers using the "update" button on the desktop, but some error must have occured during the process because when I restarted the machine the X server failed to load.

I can get to a bash shell by starting the system in recovery mode, but I have absolutely no idea what to do with it to restore the graphical frontend to the operating system.

Any ideas where to go from here?

---

### Post by crashcoredump on 2008-04-01
Can you restart the system in Safe Video mode?

In the future anytime you do anything related to video copy the contents of you xorg.conf to a location that can be restored if something goes wrong.


Something simple like 
```
$ sudo cp /etc/X11/xorg.conf   xorg.conf_BAK
```

This was you can undo the change by renaming _BAK to the filename and logging off and back on and you should be fine.

What happens when you type, startx? 
Please look in your home directory and in the X11 directory in the event the tool you used to make the change made a back-up. The Nvidia settings tool sometimes creates a file in your home dir. 

Thanks

---

### Post by Will Walshe on 2008-04-01
The startx command returns an error saying: 

"Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
        after 0 requests (0 known processed) with 0 events remainin."

There was a file named xorg.conf.backup in the X11 directory, so I renamed this to xorg.conf (after backing up the broken one, just for posterity). Didn't solve the problem though.

On restart, the X server returns an error message ending in:

"FATAL: Could not open
'/lib/modules/2.6.20-16-generic/volatile/nvidia.ko' : No such file or directory

(EE) NVIDIA (0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA (0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found "

Cheers for the help

---

### Post by forrestcupp on 2008-04-01
Go to recovery mode and type
```
dpkg-reconfigure -phigh xserver-xorg
```
Then type **start x** and see what happens.  If it still doesn't work, try the same command again only without the **-phigh**.  Doing that will make you go through the whole setup.  You can choose the vesa drivers and worry about getting the right drivers working after you get back to your desktop.

Edit:
Did you happen to have drivers installed with Envy, and maybe your kernel got upgraded or changed?  If so, boot to your recovery mode and type
```
envy --uninstall-all
```
Then to reinstall the drivers correctly with Envy, type
```
envy -t
```
But that's only if you used Envy to begin with.

---

### Post by jtrindle on 2008-04-01
It sure looks as if a kernel upgrade lost the nVidia driver.

Does the grub menu have more than one version of the kernel?  If so, try to select the older version of the kernel.

Look under /lib/modules, to see if you have an older /lib/modules//lib/modules/2.6.##-##-generic/volatile/ directory. You might be able to get away with copying the nvidia.ko file from there to the /lib/modules/2.6.20-16-generic/volatile/ directory.

If this doesn't work I go along with the suggestion of booting into safe video mode.  Then you can re-install the restricted nVidia driver.

---

### Post by Will Walshe on 2008-04-02
Thanks guys, the **dpkg-reconfigure -phigh xserver-xorg** command got me back in business. 

What did that actually do, out of interest?

---

### Post by forrestcupp on 2008-04-02
It automatically reconfigured *only* the video settings part of xorg.  Xorg also handles other things, too, like input.  If you leave the **-phigh** out, it will guide you through manually telling it what the settings should be for every part of X.

---

