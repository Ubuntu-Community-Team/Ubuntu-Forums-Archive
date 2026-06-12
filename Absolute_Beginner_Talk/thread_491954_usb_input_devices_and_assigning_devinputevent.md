---
title: "usb input devices and assigning dev/input/event"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by stil on 2007-07-04
Hey guys

I finally got my wacom tablet working on my old system by changing the values "dev/wacom" to "/dev/input/event3" in xorg.conf

I tried this on my laptop but have run in to a problem. The laptop has 4 usb ports, and being a laptop I tend to be removing adding a lot of usb devices. Things get problematic when I try to assign an input event to the tablet in xorg.conf, as I can't figure out any pattern for which input event number it's going to recieve. Usually it's either 2 or 3. I've tried unplugging/plugging in the mouse, usb stick and tablet in a few different orders. They always seem to be getting a random number assignment (my old system always assigns dev/input/event3 to the tablet)

I need a way to predict the assignment, or a way to fix an event number to the tablet, or it wont initialise on bootup :(

---

### Post by stil on 2007-07-04
bump

---

