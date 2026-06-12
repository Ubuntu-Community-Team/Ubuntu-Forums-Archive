---
title: "Help! Is nvidia GeForce driver version 87xx really stable?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by muxecoid on 2006-06-20
My GF6800LE worked fine under nvidia driver 76xx. Than I upgraded the OS and the driver (to 1.0-8762) as well. Under SuSE linux I had freezes after tens of minutes of work. The screen image did not change and only mouse pointer moved. CTRL+ALT+BkSpace did not help. I thought that it's SuSE bug and installed Ubuntu. Screen freezes still happen.

I think that the problem is in nvidia driver cause:
1. The problem is absolutly the same under different distros and I did not see it under earlier drivers.
2. Also the mouse pointer moves and HDD indicator blinks.

Is it true? Is there any way to fix the problem?

The only thing I changed in x-conf is nv->nvidia. Quote from xorg.conf
```
Section "Device"
	Identifier	"NVIDIA Corporation NV40.2 [GeForce 6800 LE]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection
```

---

### Post by tseliot on 2006-06-20
Try point 4 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

---

### Post by muxecoid on 2006-06-20
Thanks. Added
```

Option "NvAGP" "0" 
Option "RenderAccel" "Off" 
Option "IgnoreDisplayDevices" "DFP,TV" 
Option "NoRenderExtension" "Off" 
Option "AllowGLXWithComposite" "Off"

```

Would it harm performance in 2D? In 3D?

Are there any 3D benchmarks for linux?

---

