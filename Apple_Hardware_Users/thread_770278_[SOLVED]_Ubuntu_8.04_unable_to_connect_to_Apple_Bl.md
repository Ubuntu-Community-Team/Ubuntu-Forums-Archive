---
title: "[SOLVED] Ubuntu 8.04: unable to connect to Apple Bluetooth Keyboard"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by sanjinko on 2008-04-27
When browsing Bluetooth devices from menu bar in Ubuntu 8.04, I clearly see the keyboard, but keep getting this message:

Couldn't display "obex://[00:1D:4F:A6:37:D1]/".

Error: Host down

Please select another viewer and try again.

I have tried writing some commands in Terminal, without success.

Does anybody know what to do to make Apple Wireless Keyboard recognizable in Hardy Heron?:confused:

---

### Post by cyberdork33 on 2008-04-27
they completely changed the bluetooth stack in Hardy.

Open bluetooth preferences, and go to the second tab on that screen. Check input devices is not already and select it. another section will show up underneath. use the add button to add a new bluetooth keyboard/mouse.

I can't get it to work with my keyboard, but other say it works fine, so good luck. I posted my findings here:
[http://ubuntuforums.org/showthread.php?t=720139](http://ubuntuforums.org/showthread.php?t=720139)

---

