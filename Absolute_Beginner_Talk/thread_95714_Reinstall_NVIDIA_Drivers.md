---
title: "Reinstall NVIDIA Drivers"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by Kimm on 2005-11-27
A couple of days ago I was informed that there where several updates available, so I downloaded and installed these. One of these was a Kernel Update.
My NVIDIA driver is installed from source and as soon as I rebooted after the update, my X crashed ofcourse. I downloaded the Kernel source tree and recompiled the driver... no luck, I tried installing nvidia-glx from the repositories... no luck. Now, I have managed to come up with some strange mix of repository and built from source drivers and it works... somewhat, anything that uses GLX or OpenGL will not work, glxgears segfaults and no games will run.

I was woundering if there is a way that I could completely remove the driver and then reinstall it (reinstall in any way, I dont care if its by repository or source)

Can anyone please help?

---

### Post by Kimm on 2005-11-27
No problems... I seem to have fixed it on my own.

I opened Synaptic and found the nvidia-glx package, opened the "Installed Files" info window and manualy removed everything with GL or Nvidia in its name, then I did a complete removal, after that, I went looking for the restricted modules package and removed anything that had to do with NVIDIA manualy, then did a complete removal of that package aswell.

After that was done, I killed the X-server and ran the NVIDIA install script with the --uninstall argument to remove anything that might remain. After that was done, I ran the script again to install the driver.

Now, even after rebooting everything seems to be working fine, glx gears is running again and I can play games ^^

I hope this might help someone else.

PS.
I also set "Lock Version" on all the Linux Image packages to prevent this from happening again.

---

### Post by Norred on 2005-11-27
How do you quit X server???  I quit it in mandriva linux and it quit my session all together.. then of course when i log in, it starts up again.  So if i log into fail safe im guessing x server wont start since x server is like essentially the gui?


P.S.  im wondering if that is the same for Ubuntu.. b4 i try it

---

### Post by Xian on 2005-11-27
[QUOTE=Norred]How do you quit X server???  [/QUOTE]
Ctrl + Alt + Backspace with quit/restart X.

Ctrl + Alt + F1 will drop you to a command prompt.
From there issue these commands to quit/restart.

$ sudo invoke-rc.d gdm stop
$ sudo invoke-rc.d gdm start

Or to immediately restart:

$ sudo invoke-rc.d gdm restart

---

