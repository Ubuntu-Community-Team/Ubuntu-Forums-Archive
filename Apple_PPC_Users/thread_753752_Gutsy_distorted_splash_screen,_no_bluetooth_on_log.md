---
title: "Gutsy distorted splash screen, no bluetooth on login"
date: 2008-04-13
forum: Apple PPC Users
---

### Post by garbageguts on 2008-04-13
Hello Ubuntu Forums,

I decided to install Ubuntu 7.10 on an iMac G5 for fun, and have installed it using the alternative CD and the "install video=ofonly" boot command. But I've run into a couple of issues that I cannot figure out how to fix by myself.

Firstly, upon starting up the Ubuntu splash screen is distorted and funny colours. This is just a cosmetic issue and the colours fix themselves once the login screen appears, but if there is a fix I would appreciate it.

Secondly and more importantly my Apple Wireless Keyboard doesn't work on the login screen (meaning I can't log in). This is strange because I could type things fine in the alternative install (which I had to use because the Live CD wouldn't recognise my keyboard either). I was wondering if there was some command I could type in at boot to make it work... But if necessary I can go and buy a $10 USB keyboard tomorrow.

Please forgive my less-than technical word choice. I am new to Ubuntu and linux in general (but I'm willing to learn).

---

### Post by stream303 on 2008-04-13
> **garbageguts said:**
> I decided to install Ubuntu 7.10 on an iMac G5 for fun, and have installed it using the alternative CD and the "install video=ofonly" boot command.

Welcome!  I wonder what size screen and what model your iMac is - mine is an early G5 (no light-sensor, no camera) 20" display.  With mine, I never had to use any kernel parameters, even with Hardy (but that could change...) :)

> Firstly, upon starting up the Ubuntu splash screen is distorted and funny colours.
You are right - it is cosmetic and can be fixed - I forgot what thread I put that in.

> Secondly and more importantly my Apple Wireless Keyboard doesn't work onthe login screen (meaning I can't log in).
I'd definitely keep a wired keyboard handy just in case.  At any rate, you might want to try some of the tips here:

[https://help.ubuntu.com/community/BluetoothInputDevices](https://help.ubuntu.com/community/BluetoothInputDevices)

> I am new to Ubuntu and linux in general (but I'm willing to learn).

Welcome aboard!

---

### Post by garbageguts on 2008-04-14
> **stream303 said:**
> Welcome!  I wonder what size screen and what model your iMac is - mine is an early G5 (no light-sensor, no camera) 20" display.  With mine, I never had to use any kernel parameters, even with Hardy (but that could change...) :)


Mines a 20" revision B with the light sensor (no camera). I had to use that "video=ofonly" kernel parameter (now I know what it's called) otherwise I would get the "pink screen of death".

> 
You are right - it is cosmetic and can be fixed - I forgot what thread I put that in.


Excellent, I'll do a search of topics you've posted in then (hope you don't mind me spying).

> 
I'd definitely keep a wired keyboard handy just in case.  At any rate, you might want to try some of the tips here:

[https://help.ubuntu.com/community/BluetoothInputDevices](https://help.ubuntu.com/community/BluetoothInputDevices)


I tried the suggestions on that link but it's a bit impossible when I can't get past the login screen. I tried it again while using the Live CD but the Bluetooth Preferences just wouldn't see my keyboard. The keyboard in question has had a long history of losing it's connection in Tiger so maybe it was just on the blink anyway.

I bought a nice new Logitech Ultra-flat keyboard that looks very swish (and that's saying a lot as a Mac user). Works fine except for a lack of brightness control.

> 
Welcome aboard!

Thanks! I was told me the Ubuntu community was friendly :) Hopefully I can be of use once I'm sorted out. My next challenge is getting screen brightness and Airport wireless working (don't worry, I'll search first).

---

### Post by stream303 on 2008-04-14
There's definitely no rtfm here, so no worries.

I've had a few energy drinks earlier in the day and found my original posting:
[http://ubuntuforums.org/showthread.php?t=687231&highlight=splash+screen](http://ubuntuforums.org/showthread.php?t=687231&highlight=splash+screen)

Honestly, the novelty of it wore off pretty fast, and I actually use the kernel parameter of **nosplash** so I can see the boot messages scroll by instead.  Not only that, but things have changed a bit now with Hardy...

Glad to see another G5 iMac, especially the ALS model.

Unfortunately, I've never been able to get my screen brightness adjustable - thanks to nvidia keeping the good docs to themselves...

The only semi-workaround I found was to alter my gamma - play around with values from 0.5 to 1.5  (1 is the default)

```
xgamma -gamma 0.8
```
for instance.
When I found a value I liked, I made it permanent in my /etc/X11/xorg.conf.  See this thread for more details:
[http://ubuntuforums.org/showthread.php?t=710026](http://ubuntuforums.org/showthread.php?t=710026)

Be careful if you edit photographs and forget about this custom gamma used solely to tweak brightness levels.  It's not the real way to do it, but it might help if the monitor is just on the edge of annoying.

---

### Post by garbageguts on 2008-04-14
> **stream303 said:**
> Unfortunately, I've never been able to get my screen brightness adjustable - thanks to nvidia keeping the good docs to themselves...

Aha! But mines an ATI Radeon 9600 128MB. Does that make any difference (or is ATI just another money-grubbing company)? ;)

Thanks for the splash screen link, my search-fu is lacking.

---

