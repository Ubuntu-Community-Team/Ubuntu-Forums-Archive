---
title: "Installing video driver"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by darvina on 2006-06-13
Hi 
i have just installed unbuntu.  I try to change My screen resolution.  in  system preferences screen resolution.  It only showing 640*420.  How do i upgrade the drivers for Dell 1000 pc intergrated video.  Where do i get the drivers from?
thanks

---

### Post by taurus on 2006-06-13
Is that the Intel integrated video controller crappy thing from Dell that you have on your machine?  If it is, then change the "Driver" from whatever it is right now in /etc/X11/xorg.conf, probably vesa, to "i810" for your video card then.  
```

sudo gedit /etc/X11/xorg.conf

```
Now, scroll down until you get to the Section Device and replace the Driver to i810...
```

Driver      "i810"

```

---

### Post by darvina on 2006-06-13
Thanks
But it says 810 is configured
any other ideas.  There definatley is no other resolution on screen resolution setting tab


Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

---

