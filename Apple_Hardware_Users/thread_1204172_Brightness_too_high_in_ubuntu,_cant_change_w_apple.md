---
title: "Brightness too high in ubuntu, cant change w/ apple keyboard as in os x or windows xp"
date: 2009-07-04
forum: Apple Hardware Users
---

### Post by eacls86 on 2009-07-04
I am running ubuntu 9.04 on my intel mac via bootcamp and i can't change the brightness with the f1 and f2 keys and it is far too bright for my liking

thanks

---

### Post by Bucky Ball on 2009-07-04
Try right clicking on the top toolbar, 'add to panel' and you should be able to add a brightness applet which will allow you to adjust screen brightness.

---

### Post by derekeverett on 2009-07-04
I'm using a mac keyboard on an HP machine just cause I like the keyboard. I got real used to them over the years using a mac.

I've never bothered with bootcamp so I'm not sure if this will help or not but on my HP box if I hold down the fn key (beside home key) and press function keys I get some of the normal mac intended functionality.

---

### Post by eacls86 on 2009-07-04
Try right clicking on the top toolbar, 'add to panel' and you should be able to add a brightness applet which will allow you to adjust screen brightness.

Has no effect - there is a red circle with a red line thru it over the icon, plus its setting as at the bottom so if it did work it would only make it brighter

thanks all the same

---

### Post by eacls86 on 2009-07-04
I'm using a mac keyboard on an HP machine just cause I like the keyboard. I got real used to them over the years using a mac.

I've never bothered with bootcamp so I'm not sure if this will help or not but on my HP box if I hold down the fn key (beside home key) and press function keys I get some of the normal mac intended functionality.

-------

tried that all already :)

the volume f keys still work (f10 - 12) as does the eject key (without holding fn)

but thanks all the same

too future posters - i don't care whether or not the solution involves using the keyboard - i just want to be able to change the brightness of my monitor (as opposed to the brightness in linux) with a pc monitor this would be as simple as pressing a button on the monitor itself as you all know

and sorry if my sentences don't make sense because its hard to concentrate with these sore eyes lol

---

### Post by derekeverett on 2009-07-04
Did you see this?

[http://ubuntuforums.org/archive/index.php/t-1010532.html](http://ubuntuforums.org/archive/index.php/t-1010532.html)

---

### Post by eacls86 on 2009-07-04
sudo modprobe mbp_nvidia_bl
returns
FATAL: Error inserting mbp_nvidia_bl (/lib/modules/2.6.28-13-generic/kernel/drivers/video/backlight/mbp_nvidia_bl.ko): No such device

echo 150 | sudo tee /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
returns
tee: /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness: No such file or directory
150

thanks

---

### Post by 456 on 2009-08-03
Hi eacls86,

To quote you:
"too future posters - i don't care whether or not the solution involves using the keyboard - i just want to be able to change the brightness of my monitor (as opposed to the brightness in linux) with a pc monitor this would be as simple as pressing a button on the monitor itself as you all know"

The monitior you refer to is obviously a laptop monitor. "as opposed to the brightness in linux" - I not sure what this means.

This is the advice I've given to similar posts (today).

Have you tried setting the brightness options in the power management program?

Accessed via: System - Preferences - Powermanagement.

I've just fixed my laptop after getting annoyed that the screen kept adjusting to 50% brightness on battery power.

I came to your thread eacls86, seeking an answer but eventually found it by searching for "adjust brightness" in the built-in ubuntu help (accessed via: system - help and support). Please don't read that as being condescending - I searched there weeks ago but used the wrong search words.

Hope I've helped,

456

---

### Post by sargenme on 2010-04-09
I have the same problem. Using a MacBook with dual boot. None of the suggestions so far work for me.

---

### Post by linuxopjemac on 2010-04-09
Start here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

Probably pommed will do what you want:
```
sudo apt-get install pommed
```

---

