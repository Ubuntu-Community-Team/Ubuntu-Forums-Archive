---
title: "Brightness issue on Macbook 5.5"
date: 2011-08-16
forum: Apple Hardware Users
---

### Post by Jaxilian on 2011-08-16
Hi all
Brightness buttons work, but Ubuntu cannot remember the setting when I have adjusted it to what i want.
Each time the screen dims down and comes back it is slightly darker. It goes on like that until it is very dark. It doesn't matter if I put it to brightest setting.

Any fix for this?

---

### Post by scorp123 on 2011-08-16
Are you using **pommed**?

---

### Post by Jaxilian on 2011-08-17
yes

---

### Post by scorp123 on 2011-08-17
My MacBook Pro is a "5,4". So it should be similar to your's? I use the "MacTel" repo as per Ubuntu's guide on Apple hardware and I don't have any issues with my MacBook Pro (... except maybe that NetworkManager is slower than its OS X counterpart at picking up WiFi connections after resuming the laptop from a suspend ...), it's working tip top. Here is my **/etc/pommed.conf**:

```
#
# Configuration file for pommed
#

# General configuration
general {
	# fnmode: functions keys first (no need to use fn) or last
	# Value is either 1 or 2, effect is hardware-dependent
	fnmode = 2
}

# sysfs backlight control
# nVidia machines, will fall back to nv8600gmt if not supported by the kernel
lcd_sysfs {
	# The sysfs backlight control is a generic interface provided
	# by the Linux kernel for backlight control on most graphic cards.
	# The brightness range can differ depending on the hardware.

	# initial backlight level [12] (0 - 15, -1 to disable)
	init = -1
	# step value (1 - 2)
	step = 1
	# backlight level when on battery [6] (1 - 15, 0 to disable)
	on_batt = 6
}

# ATI X1600 backlight control (MacBook Pro v1 & v2)
lcd_x1600 {
	# initial backlight level [200] (0 - 255, -1 to disable)
	init = -1
	# step value (1 - 127)
	step = 10
	# backlight level when on battery [80] (1 - 255, 0 to disable)
	on_batt = 80
}

# Intel 945GM, 965GM backlight control (MacBook v1-v4, MacBook Air v1)
lcd_gma950 {
	# initial backlight level [0x6f] (0x1f - 0x94 usually, -1 to disable)
	init = -1
	# step value (0x01 - 0x20)
	step = 0x0f
	# backlight level when on battery [0x40] (0x1f - 0x94 usually, 0 to disable)
	on_batt = 0x40
}

# nVidia GeForce 8600M GT/9400M/9600M GT backlight control
# (MacBook Pro v3-v5, MacBook v5, MacBook v2)
lcd_nv8600mgt {
	# initial backlight level [12] (0 - 15, -1 to disable)
	init = -1
	# step value (1 - 2)
	step = 1
	# backlight level when on battery [6] (1 - 15, 0 to disable)
	on_batt = 6
}

# Audio support
audio {
	# Use amixer or alsamixer/alsamixergui to determine the sound card
	# and the mixer elements to use here.

	# sound card to use
	card = "default"
	# initial volume [80] (0 - 100%, -1 to disable)
	init = -1
	# step value (1 - 50%)
	step = 10
	# beep on volume change
	beep = yes
	# mixer element for volume adjustment
	volume = "PCM"
	# mixer element for muting the speakers
	speakers = "Front"
	# mixer element for muting the headphones
	headphones = "Headphone"
}

# Keyboard backlight control
kbd {
	# default value for automatic backlight (0 - 255)
	default = 100
	# step value (1 - 127)
	step = 10
	# ambient light thresholds for automatic backlight (0 - 255)
	on_threshold = 20
	off_threshold = 40
	# enable/disable automatic backlight
	auto = no
	# idle timer - switches off keyboard backlight automatically (timeout in seconds, -1 to disable)
	idle_timer = -1
	# idle tickms - timer tick rate in milliseconds
	idle_tickms = 200
}

# CD/DVD drive ejection
eject {
	# enable/disable eject key
	enabled = yes
	# CD/DVD device
	device = "/dev/dvd"
}

# Beeper
beep {
	# enable/disable beeper
	enabled = no
	# WAV file to use (from pommed: goutte.wav or click.wav in /usr/share/pommed)
	beepfile = "/usr/share/pommed/goutte.wav"
}

# Apple Remote - deprecated
# Note: the appleir driver is required for this to work; this driver has been
# obsoleted with Linux 2.6.22, so unless you are running a kernel < 2.6.22 or
# use the appleir driver on a newer kernel, this won't work.
# You should use LIRC instead.
appleir {
	# enable/disable the appleir support
	enabled = no
}


```

---

### Post by Jaxilian on 2011-08-17
thanks!
Only row that was different was:

```
fnmode = 2
```

Made it nicer to have F-keys back again.
Gonna check if it solves my issue.

---

### Post by Jaxilian on 2011-09-03
Not solved, still goes darker and darker.

If I have had power cable in and pull it, it goes superdark even though I had it brighter...a lot brighter earlier.

Weird problem.

---

