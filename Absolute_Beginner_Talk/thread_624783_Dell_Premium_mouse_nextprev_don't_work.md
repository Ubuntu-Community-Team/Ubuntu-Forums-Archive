---
title: "Dell Premium mouse: next/prev don't work"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Breepee on 2007-11-27
I got a Dell Premium mouse (no Dell hardware other than that). It has the basic buttons/scrollwheel and a set of next/previous buttons on the side. Currently they don't work (I want to use them to go forward or backwards though internetpages in Firefox and images in EoG).

Any ideas how to get it to work? In the Hotkey conif utility there's no option to set keys for next/prev.

---

### Post by PurposeOfReason on 2007-11-27
To get it with firefox, go to the mouse section in your xorg.conf (sudo gedit /etc/X11/xorg.conf) file and change it to:

```
Section "InputDevice"
   Identifier     "Configured Mouse"
   Driver         "mouse"
   Option         "CorePointer"
   Option         "Device" "/dev/input/mice"
   Option         "Protocol" "ExplorerPS/2"
   Option         "ZAxisMapping" "4 5"
   Option         "Emulate3Buttons" "true"
   Option         "Buttons" "7"
   Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

Make a backup first too (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak).

---

### Post by Breepee on 2007-11-27
I tried that, but that didn't change anything. The protocol btw is on "ImPS/2" in my xorg.conf. Could that be it?

---

### Post by PurposeOfReason on 2007-11-27
First, you did restart X? If not, do so, if so, read on.

> **Breepee said:**
> I tried that, but that didn't change anything. The protocol btw is on "ImPS/2" in my xorg.conf. Could that be it?
There's a really easy way to find out. Just write down that one line so that if it kicks you to the command line, you can edit it there and change it back.

---

### Post by Breepee on 2007-11-27
Yep, I restarted X (I'm not that new ;)).

OK, just changed it to ExplorerPS/2 and all works very fine! Excellent, thanks!

---

### Post by Breepee on 2007-11-27
I tried to use Google to learn about these protocols, but my search didn't turn up anything. Is there some list of these protocols and is it logical that some work and some don't? Is there any reason at all for xorg to configure my mouse to ImPS/2, while that works less good than ExplorerPS/2?

---

### Post by Breepee on 2007-11-27
The buttons still do not work in Nautilus btw.

---

### Post by PurposeOfReason on 2007-11-27
I never got them to work with anything but internet browsers.

---

