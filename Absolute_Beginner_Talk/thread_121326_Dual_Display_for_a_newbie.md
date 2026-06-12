---
title: "Dual Display for a newbie"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by wwbdd on 2006-01-24
I am pretty new to linux, but all of what I have seen and done is soo much better than windows.  I just finished setting up my main computer with dual boot, but when restarted with my second monitor that I use in windows, everything breaks.  It gets through the boot process fine, displaying the same thing on both screen, same as windows, but then when it's done booting up, all I get is the ubuntu sound that usually goes with the login screen.  The way i have it setup is an nvidia GeForce 5600xt with two monitors attached.  The main monitor, in the vga slot, is an lcd and the monitor displays "out of range" on the monitor.  The crt, which is plugged into the dvi slot with an adapter, is like a black and white mess, almost in a woven pattern.  If anyone could offer any advice as to how to get this to work in linux that would be wonderful.

---

### Post by mental_noise on 2006-01-24
hi, i too am a newbie but i have experienced the same problem regarding the display as "out of range". i think it is because the default resolution is out of range. i don't have a dual display set-up but i think it is because of the driver installed for your video card. now i don't know how to install drivers for you video card but what i did to temporarily remedy this problem was to press 

```
Ctrl + Alt + -
```

repetitively till i got it to display the desktop.

or you can edit your [FONT="Courier New"]**/etc/X11/xorg.conf**[/FONT] *(i am not sure if this is the correct path)* file and set the correct resolutions for your display.

hope this helps! :smile:

---

### Post by Mustard on 2006-01-24
With regards to twinview these threads might give you some assistance.  I don't know about the problems you're having with your display atm.  They might be a totally different problem.
[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)
[http://ubuntuforums.org/showthread.php?t=85769](http://ubuntuforums.org/showthread.php?t=85769)

---

### Post by autocrosser on 2006-01-25
Also--search thru the forums--there is a wealth of info that you can use--I normally help set-up ATI dual monitors--but there are many of us that can help with Nvidia cards---

Mental_noise--you are right--it's /etc/X11/xorg.conf  but, please read the info available on the forum before working with xorg--editing the conf is fairly simple-----but you can really farg your system with the wrong way:rolleyes:.

---

