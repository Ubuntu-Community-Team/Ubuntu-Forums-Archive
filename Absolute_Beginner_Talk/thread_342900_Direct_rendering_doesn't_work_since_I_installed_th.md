---
title: "Direct rendering doesn't work since I installed the fglrx driver"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2007-01-20
I have a Radeon 9600 XT and decided the other day that I was going to get beryl up and running on it.  I got everything working surprisingly well in under half an hour by changing a few things in xorg.conf:

Section "Device"
	Identifier	"ATI Radeon 9600XT"
	Driver		"radeon"
	Option		"AGPFastWrite" "yes"
	Option		"AGPMode" "4"
	Option		"ColorTiling" "on"
	Option		"EnablePageFlip" "true"
	Option		"AccelMethod" "EXA"
	Option		"XAANoOffScreenPixMaps"
	Option		"RenderAccel" "true"
	Option		"DRI" "true"
	BusID		"PCI:1:0:0"


(Note especially that I changed the driver from "ati" to "radeon") However, it was still a bit slow so I decided to install the binary drivers.  I downloaded and ran the installer, changed the driver to fglrx in xorg.conf, and rebooted.  When I started beryl, everything pretty much crashed, so I tried to change back to using radeon.  Howevr, now glxinfo says that rendering = no.  Does anyone know how I can fix this without reinstaling Ubuntu?

---

### Post by lamego on 2007-01-20
The "radeon" and "ati" drivers do not provide direct rendering, you will need fglrx .

---

### Post by meng on 2007-01-20
In case you need a guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by crazybrit4967 on 2007-01-20
> **lamego said:**
> The "radeon" and "ati" drivers do not provide direct rendering, you will need fglrx .
Then why did beryl/AIGLX work before with the radeon drivers?

---

### Post by sloggerkhan on 2007-01-20
I have beryl working with ATI / Radeon drivers/ What you need to do is use AIGLX instewad of XGL. Keep DRI off, though.

---

### Post by sloggerkhan on 2007-01-20
Edit: if youare switching to fglrx, than what I said doesn't apply,

---

### Post by crazybrit4967 on 2007-01-20
> **sloggerkhan said:**
> Edit: if youare switching to fglrx, than what I said doesn't apply,No... I tried to switch to fglrx, but then I switched back and it's not working.

---

