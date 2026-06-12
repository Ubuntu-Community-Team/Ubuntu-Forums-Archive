---
title: "[SOLVED] Wireless Mighty Mouse Disappeared"
date: 2008-09-27
forum: Apple Hardware Users
---

### Post by mostlyalive on 2008-09-27
On my MacBookPro 4,1 (Penryn) my wireless mighty mouse was automatically detected from when I tried Hardy on the LiveCD. (Neither Vertical nor Horizontal Scrolling ever worked, but button 1 and 2 clicks worked as did movement) After finally getting full support for my touchpad (the BCM5974) my mighty mouse is just plain not working... no movement, no clicks, nothing. I installed blueman to see if the mouse was even recognised, but blueman refuses to work (clicking Inquiry says that "Failed to start inquiry Reason: org.bluez.Error.FailedDevice or resource busy")

---

### Post by cyberdork33 on 2008-09-27
I think some people mentioned something similar in the touchpad driver thread. You should check there for more info:
[http://ubuntuforums.org/showthread.php?t=840040](http://ubuntuforums.org/showthread.php?t=840040)

---

### Post by mostlyalive on 2008-09-27
WOW... I actually [thought I] read that entire thread last night... aperently I skipped page six. Thanks for sending me back there.  Works like a charm now, in case anyone else has this issue and doesn't feel like reading through 6 pages of that thread, all that had to be done was to comment out the core pointer line for the synaptics in xorg.conf.  My Blueman program still doesn't work, but I couldn't care less.

---

