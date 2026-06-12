---
title: "X Server Errors"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-07-22
I was following the instructions for installing Beryl [here](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon).  When I got to the part where I had to restart X, the X server gave me this error:

```
Data incomplete in file /etx/X11/xorg.conf Undefined InputDevice "Synaptics Touchpad" referenced by ServerLayout

(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error
no screens found
```

I'm pretty sure that I replaced all the code that I changed, but I still get this error.

Can anyone help me?  Thanks.

---

### Post by meierfra on 2007-07-22
post the contents of  /etc/X11/xorg.conf

---

### Post by asmoore82 on 2007-07-22
find the section of '/etc/X11/xorg.conf' that looks like this:

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad"
EndSection

```

and **comment out** (add a # to the beginning of the line) the Touchpad Device to remove it from your active configuration.
it should now look like this:
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
#        InputDevice    "Synaptics Touchpad"
EndSection

```

This is a "quick and dirty" way to make your X work again (maybe) but if you are actually on a laptop your touchpad won't work until you do a more permanent fix of your xorg config.

---

### Post by asmoore82 on 2007-07-22
my bad... DUH!!

the more permanemt fix I just spoke of would be running this....

```
~$ sudo dpkg-reconfigure xserver-xorg
```

---

