---
title: "Ubuntu 13.10, Macbook Pro scripts: keyboard backlight, touchpad"
date: 2013-10-11
forum: Apple Hardware Users
---

### Post by Homo Luminus on 2013-10-11
Hi.

For a while now, I've been running Ubuntu 13.10 on a Macbook Pro. First, I had to fix wi-fi. That's working now. I still haven't figured out the nVidia drivers. But I have made two useful scripts, and thought I'd share them for people with a similar setup.

Reverse the touchpad scrolling movement:

```

#!/bin/bash

# set up touchpad
synclient VertScrollDelta=-85
synclient HorizScrollDelta=-85
#synclient FingerLow=10
#synclient FingerHigh=20

```

Adjust the keyboard backlight:
```

#!/bin/bash

# Francisco Diéguez Souto (frandieguez@ubuntu.com)
# This script is licensed under MIT License.
#
# This program just modifies the value of backlight keyboard for Apple Laptops
# You must run it as root user or via sudo.
# As a shortcut you could allow to admin users to run via sudo without password
# prompt. To do this you must add sudoers file the next contents:
#
#  Cmnd_Alias CMDS = /usr/local/bin/keyboard-backlight
#  %admin ALL = (ALL) NOPASSWD: CMDS
#
# After this you can use this script as follows:
#
#     Increase backlight keyboard:
#	    $ sudo keyboard-backlight up
#     Decrease backlight keyboard:
#	    $ sudo keyboard-backlight down
#     Increase to total value backlight keyboard:
#	    $ sudo keyboard-backlight total
#     Turn off backlight keyboard:
#	    $ sudo keyboard-backlight off
#
# You can customize the amount of backlight by step by changing the INCREMENT
# variable as you want it.

BACKLIGHT=$(cat /sys/class/leds/smc::kbd_backlight/brightness)
INCREMENT=15

if [ $UID -ne 0 ]; then
    echo "Please run this program as superuser"
    exit 1
fi

SET_VALUE=0

case $1 in

    up)
        TOTAL=`expr $BACKLIGHT + $INCREMENT`
        if [ $TOTAL -gt "255" ]; then
            exit 1
        fi
        SET_VALUE=1
        ;;
    down)
        TOTAL=`expr $BACKLIGHT - $INCREMENT`
        if [ $TOTAL -lt "0" ]; then
            exit 1
        fi
        SET_VALUE=1
        ;;
    total)
	TEMP_VALUE=$BACKLIGHT
	while [ $TEMP_VALUE -lt "255" ]; do
		TEMP_VALUE=`expr $TEMP_VALUE + 1`
		if [ $TEMP_VALUE -gt "255" ]; then TEMP_VALUE=255; fi
		echo $TEMP_VALUE > /sys/class/leds/smc::kbd_backlight/brightness
	done
        ;;
    off)
	TEMP_VALUE=$BACKLIGHT
	while [ $TEMP_VALUE -gt "0" ]; do
		TEMP_VALUE=`expr $TEMP_VALUE - 1`
		if [ $TEMP_VALUE -lt "0" ]; then TEMP_VALUE=0; fi
		echo $TEMP_VALUE > /sys/class/leds/smc::kbd_backlight/brightness
	done
        ;;
    *)
        echo "Use: keyboard-light up|down|total|off"
        ;;
esac

if [ $SET_VALUE -eq "1" ]; then
    echo $TOTAL > /sys/class/leds/smc::kbd_backlight/brightness
fi

```

You can download both scripts [here.](http://www.driewielerdigital.com/?p=27)

---

### Post by david.e.brock on 2013-10-17
Does this make it so we can use the brightness buttons and keypad backlight buttons again?

---

