---
title: "Gateway VX920 full resolution not available"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by rddaugherty on 2007-03-09
I've entered the specifications for this monitor exactly as published by the manufacturer. They are: Horizontal: 30-110kHz, Vertical: 50-160Hz

I entered these values using "dpkg-reconfigure xserver-xorg" while in recovery mode.

When I boot normally, the highest resolution offered to me is 1024x768, while my monitor is capable of up to 1600x1200. My graphics card is an Intel 82815 w/ 4Mb memory. I specified type "i810" for the graphics card and 4Mb memory. The monitor detection mode (run previously) did substitute possible resolutions higher than 1024x768, and I've left them intact each time I reconfigure.

Any ideas why I only see a maximum of 1024x768 resolution available? Thanks in advance!

Rich D.
](*,)

---

### Post by 67GTA on 2007-03-09
When you manually reconfigure you should have an option to choose which screen resolutions your monitor should display. I forget the option, it has been awhile, but I think it asks if you want to try to autodetect your monitor. If you select yes it will let you type the model info and then go to the screen where you can set your resolution modes. You can select the resolutions and they should show under SYSTEM>PREFERENCES>SCREEN RESOLUTION.

---

### Post by rddaugherty on 2007-03-10
Thanks, 67GTA, but I've been through many combinations and permutations of the reconfiguration process, all to no avail. I did discover a posting, however, which describes problems with the i810 driver (the only one I've found to work with my controller and monitor) similar to what I'm experiencing. The high-level discussion can be found here:

help.ubuntu.com/community/FixVideoResolutionHowto

I'm going to try the suggested 915resolution fix recommended under item # 4 on the page, "Intel Graphics driver (i810) won't use high screen resolutions."

Anyone else tried this fix with any success? ? ?  Anyone?

Rich D.
:confused:

---

### Post by treesurf on 2007-03-10
I've got a different Intel graphics card (950GMA), but the 915resolution worked great for me.

---

