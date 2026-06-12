---
title: "[SOLVED] 7.10 Dell inspiron 1100 problems"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by semperfiguy on 2007-11-02
I just tried to do a fresh 7.10 install from the alternate text-only cd and everything seemed to be working.  I got all the way through the first part of the install process, it told me to eject the cd and reboot.  I did this but when it rebooted all i got was a black screen and no hard drive activity.  So I tried it again and I selected the recovery mode and the startx command.  The same thing happened again.   I didn't think there would be any problems right of the bad with the graphics but I guess not.  Anyone else have trouble with this on install?

---

### Post by snickers295 on 2007-11-02
it sounds like a corrupt install to me.
md5sum your download and burn it at 4x and try the install again.

---

### Post by overdrank on 2007-11-02
> **semperfiguy said:**
> I just tried to do a fresh 7.10 install from the alternate text-only cd and everything seemed to be working.  I got all the way through the first part of the install process, it told me to eject the cd and reboot.  I did this but when it rebooted all i got was a black screen and no hard drive activity.  So I tried it again and I selected the recovery mode and the startx command.  The same thing happened again.   I didn't think there would be any problems right of the bad with the graphics but I guess not.  Anyone else have trouble with this on install?

Hi and if your system has the intel graphics that should be ok. Have you tried to reconfigure you xorg from the recovery mode ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` And set your resolutions. Then restart with ```
reboot
``` If that fails then try again in recovery mode but without the ```
-phigh
``` and choose vesa as the driver. Hope this helps and good luck!

---

### Post by semperfiguy on 2007-11-02
Even if the check cd option on the cd came back saying it was ok?

Ok I adjusted my resolution to the lowest possible just to see if it worked at all.  So it was set at 640x480.  I booted it with the normal option, then when it got to the graphics part it came up with a box saying "Ubuntu is running in low-graphics mode.   Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself."  Then there are three options configure, shutdown, or continue.

I chose continue and it went to a "noise screen" and made the gdm sound, but I have no visual.

---

### Post by snickers295 on 2007-11-02
> **semperfiguy said:**
> Even if the check cd option on the cd came back saying it was ok?

Ok I adjusted my resolution to the lowest possible just to see if it worked at all.  So it was set at 640x480.  I booted it with the normal option, then when it got to the graphics part it came up with a box saying "Ubuntu is running in low-graphics mode.   Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself."  Then there are three options configure, shutdown, or continue.

I chose continue and it went to a "noise screen" and made the gdm sound, but I have no visual.
  OKyour OK then.
its Ubuntu trying to auto configure your card and didn't do it right.
try to configure it in System>Administration>Screens and Graphics.

---

### Post by semperfiguy on 2007-11-02
But see I can't get there.  I have no graphical interface I can only work from the command line.  right now I'm just playing around with different xorg config options.  But still haven't gotten anything past a black screen.

Edit:  Using the vesa drive (at 640x480 resolution and 640x480 @ 60 hrtz refresh rate) and startx gets me this error:
     "(EE) VESA(0): No matching modes
      (EE) Screen(s) found, but none have a usable configuration

      Fatal server error:
      no screens found"

Edit2:  AHA! I got it.  I needed to switch to the i810 driver.  Thank you for your time and help.

Edit3:  On second thought maybe not. after switching the driver and running startx as root it worked fine.  was very slow but i expected that.  On reboot however I got the same black screen.  I didn't think there were seperate xorg files for each user.  So now I still need to get it to work from a regular boot up

---

### Post by snickers295 on 2007-11-02
your welcome!
anytime for a fellow Linux user.
please mark this thread as solved by using the "thread Tools" option at the top right corner of the thread.

---

### Post by semperfiguy on 2007-11-02
Well as you might have seen from my edit, theres still one more hitch.  I can start gnome by running startx from root but not during the regular boot process.  I assume the configuration is right because it works by running startx, but I don't understand why it won't work from a regular user.  

Can you normally run startx as a regular user? or is that a root only privelage.  from a regular boot there is nothing on the screen.  It's a black screen the whole time after grub menu.

---

