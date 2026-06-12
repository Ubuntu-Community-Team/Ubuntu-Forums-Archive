---
title: "iMAC G3 no display after load live CD"
date: 2006-09-18
forum: Apple PPC Users
---

### Post by cha_unacme on 2006-09-18
](*,) Please bear with me as I am new to loading Linux on a MAC.
 I loaded the Live CD that I burned today, I hav the Mac iso. At first the cd would not boot until I entered the following: 'live video=ofonly'. At this point the system booted I had a display while the list of checks were occuring. Then the screen weht black. The CD-rom was still running for a while then stopped but the display stayed off. 
I tried booting a second time and used 'Boot Live' and similar situation the system is reading the CD (audible) but no display.

what are possible causes of this?

---

### Post by Dreyco on 2006-09-19
You need to change the xorg.conf file
1. Boot up live CD holding down the C
2. At prompt type: live-powerpc
3. After loading everything the screen goes blank and you hear the CD running for about 2 - 3 minutes before you hear it stop,
4. Press CRTL-ALT-F1. This brings up the command line.
5. Now we need to edit the Xorg.conf file. 
Type: sudo nano /etc/X11/xorg.conf
6. Add a "#" at the line that says LOAD DRI. This keeps it from loading.
6a. Go to area near the bottom under "Monitor" and adjust the HorizSync to 60-60 and VertRefresh to 35-117 respectively.
7. Go to the the area (towards the bottom of the file) where the default Depth is and change it from 24 to 16.
8. Save and exit out of nano.
9. Type: sudo killall -HUP gdm
10. This will kill and restart the GUI.
11. You will get a screen resolution of 800 x 600 with 16 color depth.

When I tried that for my G3, I couldn't save it though, but maybe it'll work for you, I'm still having major issues with the clock (it is crashing all the GUI)

---

### Post by linear on 2006-09-19
Actually, you don't need to type anything at step 2 (the default of "live" is fine), and step 7 (changing color depth) is unnecessary once you disable DRI.

---

### Post by SonicJMC on 2007-09-05
Thank you!!! OMFG thank you!!!
I was tearing my hear out over it cause I had already devistated my OS X install and I have no Mac OS disk. No X, no 9, no nothing. I was like X sucks, *format* and then the damn Ubuntu wouldn't install.

---

### Post by Midwest-Linux on 2007-09-13
I am glad this was solved, my problem was slightly different. I had TWO video outlets on my G3, both would show the Mac OS. But only one would show the installation. So a entire week of posting here and hours and days of troubleshooting ...it all came down to simply having the monitor not connected to the correct video outlet. I am only posting this so that others would find a solution for this if the issue came up.

---

