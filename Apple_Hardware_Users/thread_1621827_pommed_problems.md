---
title: "pommed problems"
date: 2010-11-14
forum: Apple Hardware Users
---

### Post by watgrad on 2010-11-14
Hi - 
I just installed the pommed update from Update Manager (version 1.35-maverick-mactel1). (Ubuntu Maverick 64 bit)

I used to be able to turn the keyboard lights off on my MacBook Pro 7.1 using the function keys.  Now the lights are always on.  I can dim them, but they spontaneously jump back to the brightest level.

Is it possible to undo the update?  It seems to have broken the functionality - the older version worked better.

Wat

---

### Post by ertb on 2010-11-14
quite new to Ubuntu myself, but according to [this thread]("http://ubuntuforums.org/showthread.php?t=1078110&highlight=undo+update") some undoing is possible.

---

### Post by lael on 2010-11-14
It might have more to do with the on_threshold - I thought this was a problem too.

It uses the ambient light sensor to drive this value.  Try playing with your /etc/pommed.conf file to get what you want.

This is what I have:
```
# Keyboard backlight control
kbd {
	# default value for automatic backlight (0 - 255)
	default = 100
	# step value (1 - 127)
	step = 10
	# ambient light thresholds for automatic backlight (0 - 255)
	on_threshold = 2
	off_threshold = 40
	# enable/disable automatic backlight
	auto = yes
	# idle timer - switches off keyboard backlight automatically (timeout in seconds, -1 to disable)
	idle_timer = 60
	# idle tickms - timer tick rate in milliseconds
	idle_tickms = 200
}
```

---

### Post by watgrad on 2010-11-14
> **lael said:**
> It might have more to do with the on_threshold - I thought this was a problem too.

It uses the ambient light sensor to drive this value.  Try playing with your /etc/pommed.conf file to get what you want.


Thanks for the tip.  I was able to get it to work much better with a few tweaks.  With default = 0 I can avoid the flashing keyboard when setting it to 'off'  (The value must have gone below zero and then was reset to 10 the old default, causing the flashing keyboard when I tried to turn off the lights.)

Thanks again for your help - these forums are great.

```
# Keyboard backlight control
kbd {
	# default value for automatic backlight (0 - 255)
	default = 0
	# step value (1 - 127)
	step = 25
	# ambient light thresholds for automatic backlight (0 - 255)
	on_threshold = 2
	off_threshold = 40
	# enable/disable automatic backlight
	auto = yes
	# idle timer - switches off keyboard backlight automatically (timeout in seconds, -1 to disable)
	idle_timer = 60
	# idle tickms - timer tick rate in milliseconds
	idle_tickms = 200
}
```

---

