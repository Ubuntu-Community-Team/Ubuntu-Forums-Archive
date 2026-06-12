---
title: "help w/ Ibook G3 screen resolution"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by chriz74 on 2008-05-03
Hello, I installed ubuntu 8.04 hardy heron.. the screen resolution is stuck to 800x600 as the system doesn't recognize the ati radeon. How can I solve this problem?
I searched in the forum but I just found confusion. 
Does anyone know the final solution for that issue?

---

### Post by stream303 on 2008-05-03
Have you tried manually editing your /etc/X11/xorg.conf file, and adding a modules section that disables glx and dri - at least temporarily?  An example can be seen in this wiki for G3 iMacs, even though you are using an iBook:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Even though it pertains to 3d on the ati, there are some good general tips here:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

From there, perhaps you can then run

```
xrandr -q
```

and then set the native resolution with:

```
xrandr -s 1024x768 -r 60
```

If that works, check the gui display prefs again and see if it sticks.

Sorry to say I don't have an ati-equipped box anymore, so just something to try anyway...

---

### Post by chriz74 on 2008-05-04
thanks but that is not the way as the mode is not supported.
I found a working solution though.
This is what I added on my xorg.conf file:

Section "Device"
	Identifier	"ATI Rage 128"
        Driver          "r128"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync 60-60
        VertRefresh 43-117
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth 16
        SubSection "Display"
        Depth 16
        Modes "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by stream303 on 2008-05-05
That's great!  Does it still work if you change your two Depths-lines to 24 instead of 16?

---

### Post by chriz74 on 2008-05-05
yes it works even with 24 instead of 16.

---

