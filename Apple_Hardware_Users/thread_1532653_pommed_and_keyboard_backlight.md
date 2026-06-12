---
title: "pommed and keyboard backlight"
date: 2010-07-16
forum: Apple Hardware Users
---

### Post by XAZero on 2010-07-16
hi everyone

does anyone know how to disable the automatic keyboard backlight and make it to be on by default?

if i disable the automatic backlight the default value in pommed.conf doesn't have any efect.

this is because i dont want my keyboard backlight to be controlled by the system, i'd like to adjust it manually but i want it to be on by default.

might that be possible modifying the  on and off thresholds?

thanks 

excuse my poor English place 

macbook pro 5,5

> # Keyboard backlight control
kbd {
	# default value for automatic backlight (0 - 255)
	default = 255 #doenst have any efect
	# step value (1 - 127)
	step = 16 
	# ambient light thresholds for automatic backlight (0 - 255)
	on_threshold = 40  #cant disable?
	off_threshold = 80 #cant disable?
	# enable/disable automatic backlight
	**auto = no**
	# idle timer - switches off keyboard backlight automatically (timeout in seconds, -1 to disable)
	idle_timer = -1
	# idle tickms - timer tick rate in milliseconds
	idle_tickms = 2000 # WTF is this for?
}

---

