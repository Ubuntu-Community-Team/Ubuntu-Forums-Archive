---
title: "Solution to MacBook trackpad slowness..."
date: 2007-05-11
forum: Apple Intel Users
---

### Post by thully on 2007-05-11
In experimenting today, I inadvertently discovered a solution to the trackpad slowness issue.
However, the solution comes at a price - loss of advanced trackpad functionality (tapping/scrolling).  

What I did was actually a bit interesting - I actually experimented with straight Debian etch on my MacBook.  Debian etch does not enable the appletouch/synaptics driver by default - it instead uses the standard usbhid driver for the trackpad.  This, while negating the advanced functionality, works as well as OS X when it comes to trackpad acceleration, etc - you can even adjust it in the Mouse control panel in GNOME (and presumably KDE as well).  To do this in Ubuntu, presumably one would just blacklist the appletouch module and change xorg.conf to use a single usbhid device on /dev/input/mouse.

Anyway, I guess at the moment, one must choose between scrolling/tapping and a trackpad that doesn't move as slow as molasses.  I don't like tapping, so it's pretty much just the scrolling for me...

On that note, does anyone know how to get mouseemu to work properly for the scrolling with a key modified?

---

### Post by ronocdh on 2007-05-13
I still use Qsynaptics, and it's working very well for me. Because I wasn't able to **modprobe** it for reasons I don't quite understand, I just added the command **qsynaptics** to boot processes in my Sessions panel. Every time I boot up, I need to close the Qsynaptics window that pops up, but at least my trackpad is properly configured! Please let me know if anyone sees a better way.

---

