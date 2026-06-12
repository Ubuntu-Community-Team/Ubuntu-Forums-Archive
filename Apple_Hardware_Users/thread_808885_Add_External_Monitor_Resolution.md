---
title: "Add External Monitor Resolution"
date: 2008-05-26
forum: Apple Hardware Users
---

### Post by lijamez on 2008-05-26
During the live CD session on my Macbook I could choose my external monitor's native resolution of 1680 x 1050 but after I installed Ubuntu the maximum resolution in the "Screen Resolution" setting is only 1280 x 1024. How do I add the 1680 x 1050 setting?

My xorg.conf does not specify much about my display.
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by buschi on 2008-05-27
hey lijamez!

what does ```
xrandr -q
``` report?

sebastian.

---

### Post by lijamez on 2008-06-03
```
james@james-macbook:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected (normal left inverted right x axis y axis)
   1280x800       59.9 +   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1280x1024      75.0*    59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
TV disconnected (normal left inverted right x axis y axis)

```


Edit:
I don't know why, but the resolution has mysteriously appeared. 
```
james@james-macbook:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected (normal left inverted right x axis y axis)
   1280x800       59.9 +   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
TV disconnected (normal left inverted right x axis y axis)
```

---

