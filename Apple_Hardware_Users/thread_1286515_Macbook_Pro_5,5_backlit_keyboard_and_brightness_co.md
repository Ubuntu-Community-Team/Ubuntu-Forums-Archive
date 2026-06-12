---
title: "Macbook Pro 5,5 backlit keyboard and brightness controll"
date: 2009-10-09
forum: Apple Hardware Users
---

### Post by charger01 on 2009-10-09
Hi, and thanks to everyone will help me.

Most of user are talking about sound issue on MBP 5,5 , but I think that the major problem concerning the LCD brightness control and backlit keyboard.

I can't be able to use F1/F2 and F5/F6 buttons to control these features, even with Jaunty and even with Karmic. I have followed instruction posted here [https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic) but without success.

Can someone help me?

---

### Post by MadEgg on 2009-10-09
What is your problem exactly? You cannot use those keys or you cannot control the brightness at all?

---

### Post by charger01 on 2009-10-09
> **MadEgg said:**
> What is your problem exactly? You cannot use those keys or you cannot control the brightness at all?

- I cannot control lcd brightness at all (and obviously I cannot use key). I can use lcd like a UV lamp... :)

- Keyboard backlight is ALWAYS off, and there isn't apparently any way to turn it on.

---

### Post by MadEgg on 2009-10-09
If you have installed the packages from the mactel PPA as mentioned in the wiki, you should at least be able to change brightness manually by using sysfs.

I created the 2 attached programs to do this automatically: kbd_brightness and lcd_brightness. They read the current value from the sysfs and increment this by the command line argument given. I made these C++ programs because scripts cannot be set setUID and to change these settings you need to be root.

So, I compiled these two programs, copied the binaries to /usr/bin as root and set them to setuid. Then I created 4 shortcuts in the menu, 'kbd_brightness 25', 'kbd_brightness -25', 'lcd_brightness 25' and 'lcd_brightness -25'. I then assigned those hotkeys and now I am able to change the brightness of both the LCD and the keyboard using hotkeys.

---

### Post by charger01 on 2009-10-09
Many thanks. Tomorrow I will give it a try.

I wonder if Canonical will think at Apple users too, and include these featers in a not_so_far future.

---

### Post by amd-64 on 2009-10-10
> **charger01 said:**
> Many thanks. Tomorrow I will give it a try.

I wonder if Canonical will think at Apple users too, and include these featers in a not_so_far future.

I hope they will. There aren't that many issues to address and not that many models.

---

### Post by MadEgg on 2009-10-10
I improved this a bit. I added a Makefile to automate the process. You should now be able to install like this

```

tar xjf adeptbrightness.tbz2
cd adeptbrightness
make
sudo make install

```

and this will install it and set proper privileges. I also added a script called adeptbrightness.sh which monitors the light sensors and adepts the LCD and KBD brightness to it, somewhat like Mac OS X does. It is not perfect but it works quite allright for me.

When run, it sources the file ~/.brightnessrc which allows each user to set its own preferences; it can include values for KBDMIN (the minimum brightness of the keyboard), KBDMAX (the maximum brightness for the keyboard), KBDTHRES (the maximum light for which the keyboard backlight is turned on), LCDMIN (the minimum brightness for the LCD) and LCDMAX (the maximum brightness for the LCD).

mine contains:

```

KBDMIN=25
KBDTHRES=25
KBDMAX=200
LCDMIN=50
LCDMAX=255

```

This file is read every time the values are adepted so you do not need to restart the script when you change the values; the results will show up once you write the file. I hope this is usable for someone, it does the job for me.

---

### Post by charger01 on 2009-10-10
Many thanks MadEgg, I will try the installer too. Unfortunatelly, today I am very busy.

Does someone knows if there are any linux distributions which support these fatures out of the box?

---

### Post by alexmurray on 2009-10-10
This really seems like a hack - the brightness keys should instead be handled by hal / udev like all normal keys...

---

### Post by MadEgg on 2009-10-10
I don't know if they should be. When I use the power management from KDE, I do get a slider which allows me to set the screen brightness. The thing is it is not mapped to the appriopriate hotkeys, XF86MonitorIncreaseBrightness and XF86MonitorDecreaseBrightness. In fact, I think it is not mapped to any keys at all. So this should definitely be changed, as should support for keyboard backlight.

Furtermore, the combination with the light sensor is not something I have seen before on any other laptops. While I do think it would be very neat to have this implemented, if that is true it would be a rather specialized feature. But then again, some people do not like the automatically adjusted brightness anyway so that wouldn't be a problem.

It might be a hack, but for now it suits my goal so I'm quite happy.

---

### Post by zatix on 2009-11-06
I am having the same problem, but when I try to compile it, throws:

~/Downloads$ gcc lcd_brightness.cc -o lcd_brightness.cc 
gcc: error trying to exec 'cc1plus': execvp: No such file or directory


any idea?

thanks

---

### Post by zatix on 2009-11-07
keeping it alive.

---

### Post by ioasw on 2009-12-24
With my MacBook Pro 5.5 karmic everything works fine except the keyboard backlight.  I have pommed installed per [https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic) but nothing.  I have tried installing and reinstalling as well.  It's a bummer because like I said EVERYTHING else works great, with very little effort after install of 9.10.  Any help on the matter would be greatly appreciated.

Here is my pommed conf if anyone needs it:

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
    init = 10
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
    init = 0x6f
    # step value (0x01 - 0x20)
    step = 0x10f
    # backlight level when on battery [0x40] (0x1f - 0x94 usually, 0 to disable)
    on_batt = 0x40
}

# nVidia GeForce 8600M GT/9400M/9600M GT backlight control
# (MacBook Pro v3-v5, MacBook v5, MacBook v2)
lcd_nv8600mgt {
    # initial backlight level [12] (0 - 15, -1 to disable)
    init = 10
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
    default = 255
    # step value (1 - 127)
    step = 100
    # ambient light thresholds for automatic backlight (0 - 255)
    on_threshold = 20
    off_threshold = 40
    # enable/disable automatic backlight
    auto = no
    # idle timer - switches off keyboard backlight automatically (timeout in seconds, -1 to disable)
    idle_timer = 60
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

### Post by [Knuckles] on 2010-03-13
> **zatix said:**
> I am having the same problem, but when I try to compile it, throws:

~/Downloads$ gcc lcd_brightness.cc -o lcd_brightness.cc 
gcc: error trying to exec 'cc1plus': execvp: No such file or directory


any idea?

thanks

This is C++ code, you need to use g++ to compile it. The error you're getting is that gcc tries to call g++, but you don't seem to have it installed.

---

