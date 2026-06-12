---
title: "Editing pommed.conf seems to have no effect on 12.04 LTS"
date: 2012-05-03
forum: Apple Hardware Users
---

### Post by clcaus on 2012-05-03
I am on a Macbook Pro 5,5 running 12.04 LTS, pommed v1.39, and Gnome Shell 3.4. Editing /etc/pommed.conf seems to have no effect on my keyboard backlight settings on startup. I have edited it to have the keyboard backlight to be off by default, but it comes back on every time I log out and stays on after login until I use the keyboard to turn it off again. All settings respond fine to keyboard presses, though. Below is the contents of my /etc/pommed.conf:

```
#
# Configuration file for pommed
#

# General configuration
general {
    # fnmode: functions keys first (no need to use fn) or last
# Value is either 1 or 2, effect is hardware-dependent
fnmode = 1
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
# disable audio support entirely
disabled = no

# Use amixer or alsamixer/alsamixergui to determine the sound card
# and the mixer elements to use here.

# sound card to use
card = "default"
# initial volume [80] (0 - 100%, -1 to disable)
init = -1
# step value (1 - 50%)
step = 5
# beep on volume change
beep = no
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
default = 0
# step value (1 - 127)
step = 10
# ambient light thresholds for automatic backlight (0 - 255)
on_threshold = 20
off_threshold = 40
# enable/disable automatic backlight
auto = no
# idle timer - fades keyboard backlight automatically (timeout in seconds, -1 to        disable)
idle_timer = 60
# idle level - level to fade keyboard to after idle_timer seconds. Defaults to     switching off.
# idle_level = 20
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
# automatically disabled if audio support disabled above
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

### Post by tobias81 on 2012-06-07
I have the same problem .... well 12.04 is apperently not using pommed anymore, so it makes sense that chaning the config doesn't have any effect but the question is where to change the value now... what is managing keyboard lighting?

anybody an idea?

thx

---

### Post by thebrodoomen on 2012-07-27
Hi,
I had the exact same problem (MacbookPro5,5 and Ubuntu 12.04) and as you said, changing the content of pommed.conf didn't have any effect.
I solved* by uninstalling pommed [sudo apt-get --purge remove pommed] and added a few lines in /etc/rc.local [sudo gedit /etc/rc.local] before "exit 0" as follows:

sleep 10
echo 0 > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness

By doing this I manually turn down the backlight after 10 seconds of startup. Don't ask me why, but without the sleep command, this script simply wouldn't work. My guess is that the keyboard backlight is initialized multiple times to maximum brightness -- even after startup -- by the system, so my script waits a few seconds to set the default (zero) backlight brightness.
Let me know if my reply was of any help :)

* the star refers to the fact that by doing this trick, when I press F5/F6 later on to modify the keyboard backlight, the keyboard backlight acts like if it was set to maximum and not minimum. I don't know if this happens to everyone though. This is not so annoying, so I don't mind it

---

### Post by CallsignBaron on 2012-07-28
> **thebrodoomen said:**
> Hi,
I had the exact same problem (MacbookPro5,5 and Ubuntu 12.04) and as you said, changing the content of pommed.conf didn't have any effect.
I solved* by uninstalling pommed [sudo apt-get --purge remove pommed] and added a few lines in /etc/rc.local [sudo gedit /etc/rc.local] before "exit 0" as follows:

sleep 10
echo 0 > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness

By doing this I manually turn down the backlight after 10 seconds of startup. Don't ask me why, but without the sleep command, this script simply wouldn't work. My guess is that the keyboard backlight is initialized multiple times to maximum brightness -- even after startup -- by the system, so my script waits a few seconds to set the default (zero) backlight brightness.
Let me know if my reply was of any help :)

* the star refers to the fact that by doing this trick, when I press F5/F6 later on to modify the keyboard backlight, the keyboard backlight acts like if it was set to maximum and not minimum. I don't know if this happens to everyone though. This is not so annoying, so I don't mind it

Well done thebrodoomen and thank you! I can confirm this works brilliantly! Late 2008 13" Macbook (Aluminum), Ubuntu 12.04/Unity. I can confirm the behavior of the F5/F6 keys, and I agree it is only a minor irritant. Keyboard backlight is off by default and can still be used manually (including the brightness adjustment). IMHO, I think this is even better than the backlight behavior in OSX.

Thanks again ~ Baron  :KS

*Update: FYI, I have noticed that after resuming from suspend, keyboard backlight returns to full bright and must be turned down or off manually. Let me know if anyone else experiences this.*

---

