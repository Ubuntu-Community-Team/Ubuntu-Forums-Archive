---
title: "[SOLVED] Imac G3 No-CD install"
date: 2009-01-03
forum: Apple Hardware Users
---

### Post by blubaustin on 2009-01-03
Hi! I have an Imac G3 600mhz 512mb of ram, 40gb hard drive. I was wondering if it was possible to do a no-cd install of ubuntu.

---

### Post by theozzlives on 2009-01-03
You can install off USB.

---

### Post by blubaustin on 2009-01-03
No usb, no discs... just some way of installing without any external hardware.

---

### Post by tiresia on 2009-01-03
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)

---

### Post by blubaustin on 2009-01-03
Go a cd burned by a buddy of mine. I can boot from the cd but no gui.  if I enter the arguement video=ofonly I can get to the terminal. I tried editing the xorg.conf file but there is no sign of sync/refresh rates, or the "load dri" thing that I had to comment out.

---

### Post by stream303 on 2009-01-04
Which version of Ubuntu are you trying to install?

This might help.

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

I tweaked my own xorg.conf to try and work with the G3 (I don't own one) - perhaps this might help

```


Section "Module"
   Disable "glx"
   Disable "dri"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"r128"
        # Driver         "ati"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	58-62
	VertRefresh	75-117
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
		SubSection	"Display"
		Depth		24
		Modes		"1024x768" "800x600"
		EndSubSection
EndSection

Section "Module"
   Disable "glx"
   Disable "dri"
EndSection

```

You might get some more valuable xorg.conf info by installing Dapper 6.06x temporarily, and using some of those values here instead.

---

### Post by blubaustin on 2009-01-04
I'm trying to install 8.04.1

I think its trying the wrong BusID, what is the right pci BusID?

Update:
In Xorg it says my bus ID is 6:3:0 but when I run lspci its says 0000:00:10.0

---

### Post by blubaustin on 2009-01-04
I really don't wany to go to an older version of ubuntu, plus I don't have a cd burner. I also don't want to drag my buddy all the way over here just to burn a cd.

---

