---
title: "Ubuntu Edgy resolution for Compaq Laptop"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by lodravah on 2007-03-06
Heyall

I've been trying different things to get my laptop to use 1280x1024 resolution. The max I can get now is 1024x768, and my display supports 1600x1200. However, the maximum resolution that shows up in "screen resolution" from "System" - "Preferences." I have xorg-driver-fglrx installed, but when I run aticonfig --initial I get this:

laptop:~$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

I've also tried editing /etc/X11/xorg.conf by adding "1280x1024" at the line of "Modes" in the screen section. See .jpg - pic. 

I am using a Compaq Presario 900 - Series
Ubuntu Edgy (6.10)
IGP 320M Chipset Integrated with ATi Radeon Mobility U1

Any help will be appreciated :)

---

### Post by dotman on 2007-03-07
did you try running

```
$ **sudo** aticonfig --initial
``` ?

---

### Post by Anthem on 2007-03-12
There are a lot of problems with the 320m series in terms of Linux performance.  I don't want to lie to you, but frankly the 320m just doesn't play nice in Linux.

You might try some of this stuff to see if that helps at all:

[http://ubuntuforums.org/showthread.php?t=310018](http://ubuntuforums.org/showthread.php?t=310018)

---

