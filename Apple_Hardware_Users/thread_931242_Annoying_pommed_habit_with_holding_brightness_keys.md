---
title: "Annoying pommed habit with holding brightness keys"
date: 2008-09-27
forum: Apple Hardware Users
---

### Post by dustynus on 2008-09-27
If I press and hold the brightness keys to dim my display completely to black out, it goes black then blips the black off and returns to being partially bright.  I then have to press the brightness all the way to the max then slowly 1 key press at a time bring it down to make it stay on black.

What sort of /etc/pommed.conf settings may make this go away?

I'm using a macbook v2 duo core hardy.

Thanks

---

### Post by hajk on 2008-09-27
I don't think it has anything to do with pommed, I can hold the dim key on my MBP 4,1 and the screen quickly goes to black and then stays that way. My settings:> 
lcd_nv8600mgt {
       init = 12
       step = 1
       on_batt = 6
}
Of course, you should use the section for the graphics card in your MB. 

Can you boot Mac OS X and check whether it dims OK there?

---

### Post by dustynus on 2008-09-27
lcd_gma950 {
	# initial backlight level [0x6f] (0x1f - 0x94 usually, -1 to disable)
	init = 0x94
	# step value (0x01 - 0x20)
	step = 0x01
	# backlight level when on battery [0x40] (0x1f - 0x94 usually, 0 to disable)
	on_batt = 0
}
kbd {
	# default value for automatic backlight (0 - 255)
	default = 0
	# step value (1 - 127)
	step = 5
	# ambient light thresholds for automatic backlight (0 - 255)
	on_threshold = 20
	off_threshold = 40
	# enable/disable automatic backlight
	auto = no
	# idle timer - switches off keyboard backlight automatically (timeout in seconds, -1 to disable)
	idle_timer = 60
}

That's what I have down, it works great in OSX.

I messed with the graphics card settings and the problem persists. Could it be from the keyboard backlight settings ?

Thanks

---

