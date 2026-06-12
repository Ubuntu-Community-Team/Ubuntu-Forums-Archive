---
title: "Problem with power managment"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by kr8 on 2007-06-21
If I leave my computer inactive for a while it seems to go to sleep or something similar and I can't find a way to wake it up.

In Power Management I have both options ("Put computer to sleep" and "Put monitor to sleep") set to never. The screensaver comes on fine and moving the mouse brings the computer back to life but is it's left for longer the monitor goes blank but the power stays on.

I'm running Ubuntu Feisty on an Acer Aspire T135 desktop.

Thanks

---

### Post by orb9220 on 2007-06-21
Yep had this problem myself.  Now try these and don't ask me why if they work they just do for some.

1) First go to screensaver and set it for 1min then go to power management and set monitor to go off at 2mins. and then wait. 

When screensaver kicks in then go to screensaver and disable. Now wait for monitor to cutoff at the 2min mark. 

Then see if monitor wakes up moving mouse if it does then go to power and change the 2min to Never. Then you may have to wait to see if that worked.

2) If this didn't solv the problem then you can try and edit your xorg.conf file and put a # in front of the line that reads **Option DPMS "True"** to [B]#Option DPMS "True"
[/B] and save your xorg.conf file and Ctrl-Alt-Backspace to restart.

3) If that doesn't do it then reboot to your bios and disabled DPMS or ACPI in bios but then you will have no power savings at all I believe and not sure if DPMS can still be used from a software point but at least your monitor should stop turning off.

Now all this is guess work and by no means am I an expert. These are things I read in the forums and have a basic understanding on how they work.

Hope one of these will solve your problem.

---

### Post by kr8 on 2007-06-22
Thanks for this. The first one seems to have worked.

---

