---
title: "Display resolution"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by johnmax on 2007-03-20
I'm new to Linux and loaded 6.10, made note during setup that the resolution should be 1024x768, booted up and only have options for 640X480 and 800X600. Performed all updates and still have the rather large fonts on the display. The monitor is an HP vz15 LCD diaplay and the graphics accelerator is a mother board Radeon 1100. I looked on the HP web site and no Linux drivers for the display and the same for ATI for this accelerator. What now? As a side note when I first looked into Linux I used the Knoppix disk and it had the proper display resolution.

Thanks.

John

---

### Post by taurus on 2007-03-20
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Pikestaff on 2007-03-20
Try this:

```
sudo dpkg-reconfigure xserver-xorg
```

Just go through and choose defaults for basically everything, but towards the end you'll get to a part where it asks what screen resolutions you would like to use.  Find the one you want (1024x768 in your case) and press spacebar to select it.  After you've finished reconfiguring xorg, reboot and it should hopefully be an option for you now...

---

### Post by blackened on 2007-03-20
I agree that you should reconfigure xorg, but I would also suggest a little manual modification. In this order preferably:

```
sudo dpkg-reconfigure xserver-xorg
```

Do as Pikestaff suggested and select the desired resolutions (using the spacebar to select, enter will take you to the next step of the reconfigure process, and this will require you to start it again), then at the end when it asks to configure your monitor it will give you a beginner, intermediate, and advanced option. Choose advanced and agree to the defaults, but say yes when it asks if it should write the hsync and vsync values to xorg.conf.

So after the reconfigure is complete, then do a 
```
gtf 1024 768 60
```
Copy the output modeline code (from the word "Modeline" forward) and insert said code into the "Monitor" section of your xorg.conf a la
```
gksudo gedit /etc/X11/xorg.conf
```

It should end up looking similar (but not exactly) to this:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

```

After that's done, either restart the xserver with ctrl-alt-backspace or just reboot, and hopefully all will be well.

---

### Post by johnmax on 2007-03-20
It worked and thanks for the help.

John Max

---

