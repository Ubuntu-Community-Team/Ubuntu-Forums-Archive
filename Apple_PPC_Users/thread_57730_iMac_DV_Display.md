---
title: "iMac DV Display"
date: 2005-08-17
forum: Apple PPC Users
---

### Post by Freddie on 2005-08-17
I have recently installed ubuntu on my (old) iMac DV. It all works fine apart from one very annoying problem, the display does not fill up the whole screen. There is a large chunk of 'unused' screen on the left and top sides of the monitor and a fair bit on the right and bottom sides. Now normally on a PC I would use the controls on the monitor to fix this and expand the display area so that it filled up the whole screen. But I can not do this on an iMac (well I am not sure how it is done) as there are no controls. This is not a ubuntu problem as such (if I got into open firmware I get the same amount of 'unused' screen) but I would like to know if there is a way to fix it. Someone said that it is to do with some data stored on the pram and that I can go into the system settings on OS 9/X to fix it, I do have an iMac restore (live) CD, but it does not give me this option and I can not do a hard disk install of OS 9 as the restore image is damaged. Can someone help me with this very annoying problem?

---

### Post by autocrosser on 2005-08-17
Try this simple one--reboot & before the "chime"--hold down <apple> <option> <p> <r>--this resets the parameter RAM (PRAM)--let the unit "chime" 3-4 times then just release the keys so the unit can boot as normal (this assumes you have a apple keyboard:)--if not, sub <alt> for <apple>). This will put ALL system values back to default & should "fix" the problem (by the way--in the Apple world this is the "four-finger salute":-)). Post back about how it went--also, search the forums for other Apple info--We have quite a few PPC users.

---

### Post by Freddie on 2005-08-17
After I heard the 'chime' I held down <control><apple><p><r> but I did not get anything the computer booted normally. Did I do it correct.

---

### Post by Freddie on 2005-08-17
I have found out how to do it (I got the keys wrong the first time). I did it like you said 4 times (so four charms in total). But it does not seem to have fixed it, is there anything else which I can do to fix this problem?
Thank you for all of your help.

*Edit* I have been looking into this and I have been told that in mac os x I can use the geometry manager to change the settings. Does such an app exist for linux which I can use? I assume that it is either stored in the firmware or the pram as it affects all os's. I have however tried resetting the firmware (reset-nvram <return> reset-all <return>), but it does not seemed to have worked.

---

### Post by autocrosser on 2005-08-18
Well--next I'd refer you the the Apple Support page--  [http://www.apple.com/support/imac/g3/](http://www.apple.com/support/imac/g3/)  --this will get you all the spec & fixes available-- I don't recall a geometry manager--but, I have not worked with iMacs much--

Hope this helps--

---

### Post by everettattebury on 2005-08-19
[QUOTE=Freddie]
*Edit* I have been looking into this and I have been told that in mac os x I can use the geometry manager to change the settings. Does such an app exist for linux which I can use? I assume that it is either stored in the firmware or the pram as it affects all os's. I have however tried resetting the firmware (reset-nvram <return> reset-all <return>), but it does not seemed to have worked.[/QUOTE]

I have a summer 2001 imac, and I noticed that the screen looked a little rotated, and I was able to fix it with the geometry tab of the OS X display system preference pane.  There is also a Classic Mac OS program called the Apple Display Adjustment Utility that you can find [here](http://www.seanano.org/apple/dau/).  I haven't been able to find a linux alternative.

---

### Post by Freddie on 2005-08-19
So, I now need a way of getting myself OS 9. I do have an apple iMac restore CD however the restore image on it does not work, but if I boot up from it I am able to get into the OS 9 ('live' version). I have a load of cruddy 10Gb apple hard disks as well. Does anyone know if it is possible to either somehow use that program within the live mode of OS 9, or install it (get an image of it?)

---

### Post by Elijahg on 2005-09-16
I saw a package called "ncurses" being installed on my iMac (it kept hanging at the configuration, so I never actually used the package) the description was "A CRT screen management and optimization utility"

Maybe you could use that.

---

### Post by mbradsha on 2005-09-18
I too had/have problems with the screen geometry on my iMac DV.  I am able to fix this by using xvidtune located in /usr/x11R6/bin, however with every reboot, the settings are lost and I must redo it.  In my case the screen is shifted right about a cm off the monitor. Part of the clock and the trashcan are not visible, and this is quite annoying.  Is there a way to make the settings permanent?


Thanks

---

### Post by shinil on 2007-03-09
I have an imac g3 400 DV, the only way to adjust the geomentry, brightness etc. is via the apple OS and this appears to be the same with all Apple displays.

I've tried shifting the geometry using the monitors control panel in os 9x, then restarting in ubuntu.
The settings appear to have been reflected in ubuntu however the os 9x screen size and position is not the same as when running ubuntu so it may require some jumping back and forth to get it right.

One sugestion I have is to try running mac on linux, then open the  os 9 or os X control panel and adjust  from there. As both ubuntu and the display controls will be available at the same time this may allow better adjustment ( i have not tested this ).

---

