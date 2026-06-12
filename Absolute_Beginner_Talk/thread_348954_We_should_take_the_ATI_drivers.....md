---
title: "We should take the ATI drivers...."
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2007-01-29
And stick them up ATI's ***!

Damn Im tired of these ******* drivers.. sorry but im pissed over this.
How hard can it be for ATI to just release some easy to install drivers?!?

Sorry..  heres my question..

How do I completely remove everything that is related with the video card drivers, so I can start over? I really would hate to reformat again.

I have both tried to install the free and the ones from ATI's website, broke my xserver 3 or 4 times, and got it back again on either one. Now im back on the ATI drivers, but with no 3d and low glxgears printfps score..

Any idea how I can remove it all, so I can try once again?

Thanks alot

---

### Post by mhueting on 2007-01-29
I'm sorry, I don't know how you would remove everything, but I do have the ultimate ATI Radeon/Ubuntu guide for you:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

It's absolutely great, and it works like a dream on my machine :) (Ubuntu Edgy with ATI Radeon 9600XT)

---

### Post by aktiwers on 2007-01-29
Thanks mhueting,
But I have tried this guide like 100 times, sadly without any luck.

Im a "lucky"  owner of a radeon 9200SE card, witch is not supported  be any drivers after 8.28.8, but still when trying to install these, it always fails.

Thanks for the suggestion though :)

---

### Post by fsando on 2007-01-29
I'm very much with you - i have a laptop with x1600 - and still beryl runs slow and sloppy.
I had a go at the 8.33.6 drivers - but reverted to the 8.28.8 as they are a lot faster. Spent half weekend cleaning after my experimenting. (I have an unanswered rant here: [http://www.ubuntuforums.org/showthread.php?t=348415]("http://www.ubuntuforums.org/showthread.php?t=348415"))


Just did a quick install of the 8.33.6 again right now (I've learned it now) but they were too slow and firegl extensions were missing (I don't know what firegl is but I guess you want it).
I uninstalled them through synaptics, after uninstall, the old 8.28.8 drivers were immediately available in synaptics so I installed them and now things seems fine (haven't tested beryl).
How I did it:
1. Download drivers from ati.com (the automated installer - name ends with *.run)
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
2. Build distro specific package (make the *.run file executable)
From a console running this command will give a list of available package formats```
*.run --listpkg
```Then this command will give the chosen package (I chose Ubuntu/6.10)```
*.run --buildkg Ubuntu/6.10
```Produces a handful of *.deb files.
I believe you want only these
xorg-driver-fglrx_8.33.6-1_i386.deb (the driver)
fglrx-control_8.33.6-1_i386.deb (ati control panel)
(numbers probably varies)
3. Uninstall old:
In synaptics look for 'xorg-driver-fglrx' and 'fglrx-control'
Remove completely
4. install new
at a terminal I started nautilus as superuser:
sudo nautilus
Browsed to the newly created packages: double-click the driver and then the control.
Now I had the new drivers
- restart x ctrl+alt+backsp
 - painting of window very slow - clearly visible steps
5. Uninstall new driver with synaptics - remove completely
6. reinstall old drivers: should be immediately available in synaptics - just choose and apply.
Restart x (ctrl+alt+backsp)

---

