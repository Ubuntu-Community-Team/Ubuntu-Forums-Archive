---
title: "My Trackpad/Touchpad Solution"
date: 2015-01-17
forum: Apple Hardware Users
---

### Post by mcoyle on 2015-01-17
Hello Gang!

One of the things about Linux I never felt was quite right on my MacBookPro6,2 was the trackpad. While typing, the cursor would randomly click on the screen leaving me with a jumbled paragraph of text. I tried all the standard programs and settings (gpointing-device-settings, dconf-editor, Mouse & Touchpad, etc.) but could never get it right. Here is my solution. I'm no expert, but maybe this will help you. This post assumes you know your way around a terminal and nano.

The driver for the trackpad is installed with this package: *xserver-xorg-input-synaptics*. It's probably installed by default, but check with the Ubuntu Software Center to make sure.

The trackpad settings are stored in: */usr/share/X11/xorg.conf.d/50-synaptics.conf*. They recommend editing a copy in another folder. The following command accomplishes that.

```

sudo cp /usr/share/X11/xorg.conf.d/50-synaptics.conf  /etc/X11/xorg.conf.d/50-synaptics.conf

```

If you get an error that */etc/X11/xorg.conf.d* doesn't exist, create it with the following command:

```

sudo mkdir /etc/X11/xorg.conf.d

```

Edit our new copy with the command:

```

sudo nano /etc/X11/xorg.conf.d/50-synaptics.conf

```

After the line: *MatchDevicePath "/dev/input/event*"*  add the following:

```

#Reverses scrolling - enables "Natural Scrolling"
        Option          "VertScrollDelta"       "-300"

#Sets the threshold for a recognized tap a little higher
        Option          "FingerHigh"            "110"
        OPtion          "FingerLow"             "100"

#Eliminates most random clicks caused by my palm
        Option          "PalmDetect"            "1"
        Option          "PalmMinWidth"        "8"
        Option          "PalmMinZ"              "275"

```

Keep in mind these settings are for my fat fingers. You may need to adjust them based on information found on the websites referenced below.

Finally, we need to tell the trackpad not to click when we're typing. It's just rude. We're going to stick a command in our home profile which will execute each time we log in.

```
nano ~/.profile
```

and add:

```

syndaemon -K -t -d

```

Re-logging in should execute all the changes. The following two web sites contain a wealth of info about tweaking the trackpad.

[https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)
[http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html)

---

### Post by rican-linux on 2015-01-17
Thanks for the info!

---

