---
title: "[SOLVED] random (?) hard crash, now res is bad"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by cifdtruckie on 2008-01-01
My system was randomly locking up pretty frequently (sometimes 15 minutes after booting up) while I was using my wireless adapter without the proper drivers.  Once I installed the drivers with ndiswrapper, everything seemed peachy.  Now this morning (at 2:57 am, according to the clock) I woke up to find the system locked up once again (3 days after I took care of the problem) and had to do a hard reboot.

My screen res. is now locked at 800x600 - I checked xorg.conf and the other resolutions are present on the "mode" line, but I can't set it back to 1024x768.

I think it might be a compiz issue (I have no video card, just the Intel onboard video) - but I have only basic effects enabled and wasn't experiencing any problems for days.

Is there any log of the crash on the system that I can look at to determine exactly what caused it, and if not, does anyone have any ideas regarding how I can keep it from happening again?

And, more immediately important, how can I get my res. back to where it needs to be?

---

### Post by kvonb on 2008-01-01
-

---

### Post by cifdtruckie on 2008-01-01
I already had screensaver and power management off, so that's not it...

I'll try your suggestion regarding the resolution when I get home from work...

---

### Post by cifdtruckie on 2008-01-01
Ok, so when I restarted the comp. again, my wireless wasn't working, so I just ran sudo dpkg-reconfigure -phigh xserver-xorg, because it seemed that the hard crash had screwed everything up.  Now, everything seems fine except for the refresh rate, so I'm just going to run sudo dpkg-reconfigure xserver-xorg and hopefully everything should be peachy...

---

### Post by cifdtruckie on 2008-01-01
Well, talk about doing things the hard way first... after reconfiguring xorg.conf, rebooting, editing it manually, and rebooting, I realized that all I had to do was run the detection tool in Screens and Graphics!

Maybe my futility will one day help the hapless user with the same issue that stumbles upon this thread.... :)

---

