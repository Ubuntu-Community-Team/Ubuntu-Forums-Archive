---
title: "pommed adjusts backlight very slowly"
date: 2010-06-26
forum: Apple Hardware Users
---

### Post by Helios747 on 2010-06-26
I have a MacBook 5,1

I've done an Ubuntu 10.04 CLI install and simply installed the packages I wanted to get the exact system I wanted.

In a vanilla ubuntu install, after installing pommed, backlight keys work as they should.

However in my setup, when I install pommed, the backlight keys do adjust the screen brightness, and gpomme shows that it does, it just does so VERY slowly.

Increasing the step value had no effect.

help?

---

### Post by GlazedWicker on 2010-06-27
I'm having the same issue except half the time it works like it should, but then i restart and it's screwed up again.

---

### Post by Zookalicious on 2010-07-02
I have this problem. Unfortunately I figured it out on my last install but can't for the life of me remember what I did on it now :/ I'm still researching so I will let you know if/when I remember it. I do unfortunately recall it involves editing the step value in a .conf file but that didn't work for me under the latest pommed and 10.04 either.

**EDIT: Problem Solved.**

Apparently the comments state that most of the step values can only go up to 2 or 127 or some value like that. With a bit of searching I found that you can input a higher value to increase the speed to an acceptable value. Here is my config file.

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
    step = 20
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
    step = 20
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
    auto = yes
    # idle timer - switches off keyboard backlight automatically (timeout in seconds, -1 to disable)
    idle_timer = 60
    # idle tickms - timer tick rate in milliseconds
    idle_tickms = 2000
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

For Macbooks v.5 I changed the step value to 20 (a good speed in my opinion, I also have a macbook 5,1) I also changed the "fallback" nv8600gmt value too just to be sure it worked, although I'm probably going to put that back now.

---

### Post by Zookalicious on 2010-07-02
For anyone else having this problem here is a step by step solution. 

- Open a terminal, type in "sudo gedit /etc/pommed.conf"
- type in your password
- Find the version of your macbook (I think this is a problem only with 5,1 but I don't know for sure)
- Change the following:
```
# nVidia GeForce 8600M GT/9400M/9600M GT backlight control
# (MacBook Pro v3-v5, MacBook v5, MacBook v2)
lcd_nv8600mgt {
    # initial backlight level [12] (0 - 15, -1 to disable)
    init = -1
    # step value (1 - 2)
    step = 1
    # backlight level when on battery [6] (1 - 15, 0 to disable)
    on_batt = 6

``` change the step value to "20" or a number around there, according to how fast you want to LCD to light up / dim.
```
# nVidia GeForce 8600M GT/9400M/9600M GT backlight control
# (MacBook Pro v3-v5, MacBook v5, MacBook v2)
lcd_nv8600mgt {
    # initial backlight level [12] (0 - 15, -1 to disable)
    init = -1
    # step value (1 - 2)
    step = 20
    # backlight level when on battery [6] (1 - 15, 0 to disable)
    on_batt = 6
```- Save the file
- Restart your machine
- You should now have a brightness slider that moves at a reasonable pace :) Go back into the file and change that number if you want it to move faster or slower. Larger numbers mean faster, smaller number -> slower. 

Hope this helps someone!

---

### Post by griffineyes on 2012-08-29
> **Zookalicious said:**
> For anyone else having this problem here is a step by step solution. 

- Open a terminal, type in "sudo gedit /etc/pommed.conf"
- type in your password
- Find the version of your macbook (I think this is a problem only with 5,1 but I don't know for sure)
- Change the following:
```
# nVidia GeForce 8600M GT/9400M/9600M GT backlight control
# (MacBook Pro v3-v5, MacBook v5, MacBook v2)
lcd_nv8600mgt {
    # initial backlight level [12] (0 - 15, -1 to disable)
    init = -1
    # step value (1 - 2)
    step = 1
    # backlight level when on battery [6] (1 - 15, 0 to disable)
    on_batt = 6

``` change the step value to "20" or a number around there, according to how fast you want to LCD to light up / dim.
```
# nVidia GeForce 8600M GT/9400M/9600M GT backlight control
# (MacBook Pro v3-v5, MacBook v5, MacBook v2)
lcd_nv8600mgt {
    # initial backlight level [12] (0 - 15, -1 to disable)
    init = -1
    # step value (1 - 2)
    step = 20
    # backlight level when on battery [6] (1 - 15, 0 to disable)
    on_batt = 6
```- Save the file
- Restart your machine
- You should now have a brightness slider that moves at a reasonable pace :) Go back into the file and change that number if you want it to move faster or slower. Larger numbers mean faster, smaller number -> slower. 

Hope this helps someone!
What would a solution for this be for a powerbook6,4 g4 1.33 with lubuntu 12.04 and nouveau?

Any help would be greatly appreciated.

---

