---
title: "3d Object Depth"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-16
Several of my screensavers have incorrect depth/positioning information. Check out the screen shot. What is going on here?

---

### Post by overdrank on 2008-01-16
> **imaginal said:**
> Several of my screensavers have incorrect depth/positioning information. Check out the screen shot. What is going on here?

HI and I have seen this once before, what is your model of graphics card have you installed drivers?

---

### Post by imaginal on 2008-01-16
```
lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```
and xorg.conf
```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection
```

---

### Post by overdrank on 2008-01-16
> **imaginal said:**
> ```
lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```
and xorg.conf
```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection
```

HI and I have the intel 945 on my laptop and it is running feisty. You may look in synaptic manager for 915 resolution as it may help. Sorry for not having more info.

---

