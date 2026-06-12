---
title: "Wrong resolution"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by samkline on 2007-11-27
Hi,

I've been using a 19" widescreen monitor with 1440x900 and it has been working well. I got a 22" widescreen 1680x1050 today and was trying to set that up. Right now both monitors are working but my secondary monitor (the old 19") is only using 1280x800.

I can't use the "System -> Preferences -> Screen Resolution" program because I get this error:
> The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

I've also tried the "Screen and Graphics Preferences" window makes it look like it is set up correctly, it says "screen 2" is using 1440x900, but I can tell by looking at it that it isn't and my monitor's on screen display feature says it is using 1280x800.

What can I do to get this working?
I am using the nvidia drivers and I have an Nvidia Geforce 7900. I do not have compiz enabled (I did before but I disabled it before setting up the second monitor)

(Edit: also thought this might be useful. I took a screen shot, but the 2nd screen is white. You can't see my desktop background or Firefox, which is running on that screen. [Link](http://img81.imageshack.us/img81/7482/weirdscreenshoteo9.png))

I'll attach my xorg.conf file.
Thanks!

---

### Post by samkline on 2007-11-27
I just realized I [have had this problem before](http://ubuntuforums.org/showthread.php?t=574963). I JUST switched from a VGA to a DVI cable on my old monitor while setting up this new monitor.

I switched back from DVI to VGA just now and it fixed my problem - now both monitors are working with the correct resolution.

Still got the screenshot problem though, but its minor.

---

