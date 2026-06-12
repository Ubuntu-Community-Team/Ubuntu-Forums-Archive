---
title: "Keyboard number lock"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-07-27
My keyboard remains in Number Lock even when it is switched off.  Is there an easy way to edit keyboard settings?  Mine is UK English.

---

### Post by Rocket2DMn on 2007-07-27
This is probably a setting in your BIOS.  You can access the BIOS at the beginning of the computer bootup sequence by pressing the correct key as displayed on the initial screen.  It usually only gives you a split second to do it, but common keys are F2, F8, F12, and DEL.  
Once in the BIOS you need to navigate around until you find the setting for NumLock (if it's there at all).
Be careful what you change in the BIOS, if you think you may have changed something on accident, exit the BIOS without saving and restart the computer again.
Hope that fixes it.

---

### Post by bugster on 2007-07-27
Thanks Rocket - trying it now

---

### Post by bugster on 2007-07-27
Must be the first BIOS I've ever had that didn't include number lock - and I've tried everything in the BIOS.  I really would appreciate a way out of this one please ???

---

### Post by Rocket2DMn on 2007-07-27
Perhaps you can configure your BIOS to cut power to the peripherals when it is powered off (even though the power cable is still plugged in).  Some computers continue to power them, but there might be a setting to change that.  Otherwise, I'm stumped.

---

### Post by bugster on 2007-07-27
Anyone else ?

---

### Post by RomeReactor on 2007-07-27
Hi. As a last resort--and knowing there's a great probability that you've tried this already--check in the back of your system's case to see if there is a **I/O** power switch in the PSU. At the moment that's the only other suggestion that comes to mind.

---

### Post by bugster on 2007-07-28
Thanks for the suggestions though I still have the problem.  I would like to edit my keyboard configuration i.e. type 102, 105 etc and see if this helps.  Is there an easy way to do this please?

---

### Post by Rocket2DMn on 2007-07-28
That option is available when you reconfigure the Xserver
```
sudo dpkg-reconfigure xserver-xorg
```
A backup of your old /etc/X11/xorg.conf file will be made in that directory, but you can manually back it up first if you want
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Try and remember your video settings since these are also reconfigured here.

---

### Post by bugster on 2007-07-28
Thanks.  Unfortunately my first attempt lost the video settings I managed to fix yesterday.  Can anyone tell me how to revert to the backup copy please?

---

### Post by bugster on 2007-07-28
> **bugster said:**
> Thanks.  Unfortunately my first attempt lost the video settings I managed to fix yesterday.  Can anyone tell me how to revert to the backup copy please?

Panic over - I've managed to restore my xorg.conf from a backup.  Now that's progress - I wouldn't have dared try that a week ago :D

Still struggling with the keyboard number lock though and I've just noticed the Caps Lock doesn't work either. :confused:

---

### Post by forestpixie on 2007-07-28
Numlock can be controlled with numlockx

sudo apt-get install numlockx

then numlockx on or numlockx off

believe it's mv, but make sure your moving the right one - I ended up with a few backed up xorg.conf files

sudo mv /etc/X11/nameofbackup /etc/X11/xorg.conf

would copy your backup to xorg.conf

---

### Post by forestpixie on 2007-07-28
missed that :)

perhaps theres a caps lock control as well

---

### Post by bugster on 2007-07-28
Thanks forestpixie.  Tried both and no change - number lock remains on even though the key seems to be working as the light on the keyboard toggles on and off.  Strangely the caps lock light doesn't work (nor does the key) though caps can be written by holding down the SHIFT key.  Still puzzled - maybe I should try a different keyboard.  This one is a CHICONY KB 0108. Grateful for any further advice.  Maybe I should have rebooted after changing the settings ??

---

### Post by Rocket2DMn on 2007-07-28
A different keyboard might help, but I wouldn't bet on it.
The reason I didn't suggest any software fix like forestpixie proposed was because the computer is actually off when you have this problem.  It still sounds like a hardware problem to me, but if you can find a way to have the computer set numlock to OFF when it shuts down, that might be do the trick (so the keyboard stays in that state since it is still receiving power).

---

### Post by bugster on 2007-07-28
Thanks Rocket.  I just tried a reboot and watched the numbers lock light as it progressed.  Twice during the boot the nums lock light came on and I switched it off.  With the light on or off nums lock is operational.  Perhaps more changes in xorg.conf are needed ??

---

### Post by Rocket2DMn on 2007-07-28
No, I don't think so, since that controls some of your hardware while the Xserver (GUI) is running, and does not help when the computer is shut down.
Perhaps there is a way to have the kernel turn off numlock when it shuts down, but to be honest, I don't know how to go about that, or if it's even possible.  I have not been able to find anything after searching google, but please feel free to look yourself.
I think the best option is to check out your BIOS again for anything relating to the providing of power to peripherals while the machine is off.  It could even be a bug in your BIOS, in which case a BIOS update may be the next order of business.

---

