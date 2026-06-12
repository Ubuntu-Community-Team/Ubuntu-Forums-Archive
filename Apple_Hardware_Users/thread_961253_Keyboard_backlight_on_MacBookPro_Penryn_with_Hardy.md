---
title: "Keyboard backlight on MacBookPro Penryn with Hardy Heron"
date: 2008-10-28
forum: Apple Hardware Users
---

### Post by BikerNiK on 2008-10-28
Hi everybody,

Since few days I've decided to test **Ubuntu Hardy Heron** on my **MacbookPro Penryn**.

Thanks to this forum, and others web pages, I manage to install it without any problems, and I've now a triple boot (with MS Vista too), fully fonctionnal.
All MacBookPro's features works very well, except one of them : **the keyboard backlight**. :neutral:

I install "***[pommed]("http://packages.debian.org/lenny/pommed")***" which is supposed to active it, but it's not works. Yet the keyboard backlight is fonctionnal because if I tape this in a terminal : ```
sudo ./keyboard_brigthness toggle
```...when I'm in the **mactel-linux-tools** folder, the keyboard backlight switch on!

But, impossible to active it automatically, like it's normally works.
Have you any ideas or suggestions to help me ? It's a kind frustating since it's the last things which doesn't work...


Thanks for any helps, and sorry if my post seems weird, I'm french and not totally fluent in english (I already posted in french forums, but no answers...). :)

---

### Post by cyberdork33 on 2008-10-28
> **BikerNiK said:**
> All MacBookPro's features works very well, except one of them : **the keyboard backlight**. :neutral:

I install "***[pommed]("http://packages.debian.org/lenny/pommed")***" which is supposed to active it, but it's not works. Yet the keyboard backlight is fonctionnal because if I tape this in a terminal : ```
sudo ./keyboard_brigthness toggle
```...when I'm in the **mactel-linux-tools** folder, the keyboard backlight switch on!

But, impossible to active it automatically, like it's normally works.
Have you any ideas or suggestions to help me ? It's a kind frustating since it's the last things which doesn't work...

There are many, many fixes for this sort of stuff but I think they are only applicable in Intrepid. See the recent threads related to this:
[http://ubuntuforums.org/showthread.php?t=959992](http://ubuntuforums.org/showthread.php?t=959992)

The Mactel-Support PPA (which contains many of the patched packages) can be found here:
[https://edge.launchpad.net/~mactel-support/+archive](https://edge.launchpad.net/~mactel-support/+archive)

---

### Post by kosumi68 on 2008-10-28
Since you are running Hardy, there are a few additional things to test, besides the suggestions on the links provided by cyberdork:

1. Is your keyboard backlight keys registered as X events? Have a look using the 'xev' application.

2. Is your machine listed in /usr/share/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi or /etc/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi? 

You might also want to run pommed with debug output (check pommed -h), to determine if the key presses are being registered.

---

### Post by kosumi68 on 2008-10-28
... and one more thing: if you are going for the intrepid-style way of adding keyboard backlight, you may want to check

1. The path to your sysfs leds device
```

find /sys/class/leds/

```

2. The path in /usr/share/hal/fdi/information/10freedesktop/10-applesmc.fdi
```

grep sysfs /usr/share/hal/fdi/information/10freedesktop/10-applesmc.fdi 

```

This method was not really done for intrepid, but if it works for you, with a modified 10-applesmc.fdi, we can update the hal-applesmc package to work for both distributions.

---

### Post by BikerNiK on 2008-10-30
Hi kosumi68 and first, thanks for your help,

I've few questions about your answers, because I'm not an Ubuntu specialist... When you said :
> **kosumi68 said:**
> 1. Is your keyboard backlight keys registered as X events? Have a look using the 'xev' application.
How can I know if my keyboard backlights keys are registered or not ? When I'm launch "xev", the results isn't very clear for me... It's only launch an application which is report in the terminal the coordinates of my mouse...

> **kosumi68 said:**
> You might also want to run pommed with debug output (check pommed -h), to determine if the key presses are being registered.
Here's the result of this command :
```
pommed configuration:
 + General settings:
    fnmode: 1
 + ATI X1600 backlight control:
    initial level: -1
    step: 10
    on_batt: 80
 + Intel GMA950 backlight control:
    initial level: 0xffffffff
    step: 0xf
    on_batt: 0x40
 + nVidia GeForce 8600M GT backlight control:
    initial level: -1
    step: 1
    on_batt: 6
 + Audio volume control:
    card: default
    initial volume: -1
    step: 10%
    beep: yes
    volume element: PCM
    speaker element: Front
    headphones element: Headphone
 + Keyboard backlight control:
    default level: 255
    step: 50
    auto on threshold: 40
    auto off threshold: 80
    auto enable: yes
    idle timer: 60s
 + CD eject:
    enabled: yes
    device: /dev/dvd
 + Beep:
    enabled: no
    beepfile: /usr/share/pommed/goutte.wav
 + Apple Remote IR Receiver:
    enabled: no
```


Sorry, but it seems to be too complicated for my level for now...

---

### Post by kosumi68 on 2008-10-30
> **BikerNiK said:**
> 
Sorry, but it seems to be too complicated for my level for now...

Not to worry. There are several threads about these things floating around currently, chances are it will be resolved anyways. Thanks for reporting!

---

### Post by cyberdork33 on 2008-10-30
> **BikerNiK said:**
> How can I know if my keyboard backlights keys are registered or not ? When I'm launch "xev", the results isn't very clear for me... It's only launch an application which is report in the terminal the coordinates of my mouse...
xev will report output to the terminal when you hit a particular key. To check that the key is "doing something", run xev, hit the key you want to check, then stop it (Ctrl+C will kill the current running item). Then you can copy and paste any output from the key presses here.

---

### Post by BikerNiK on 2008-10-31
Ok, thanks cyberdork33.
Here's the result when I press the two buttons supposed to activate or desactivate the keyboard backlight.

```
KeyPress event, serial 31, synthetic NO, window 0x2800001,
    root 0x13b, subw 0x0, time 184216, (-208,639), root:(466,690),
    state 0x0, keycode 71 (keysym 0xffc2, F5), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x2800001,
    root 0x13b, subw 0x0, time 184336, (-208,639), root:(466,690),
    state 0x0, keycode 71 (keysym 0xffc2, F5), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x2800001,
    root 0x13b, subw 0x0, time 184847, (-208,639), root:(466,690),
    state 0x0, keycode 72 (keysym 0xffc3, F6), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x2800001,
    root 0x13b, subw 0x0, time 184959, (-208,639), root:(466,690),
    state 0x0, keycode 72 (keysym 0xffc3, F6), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

