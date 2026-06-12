---
title: "Question: How can I customize my Mouse buttons?"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by eighthate on 2006-10-02
hEY I presently have a microsoft Mouse with lots of buttons including a Back and forward button on it, i wanted to know if there was a way to configure them since my mouse's buttons (back and forward) are presently detected as normal clicks( left click and right click)

Thanks :D

---

### Post by GStubbs43 on 2006-10-02
[http://www.ubuntuforums.org/showthread.php?t=219894&highlight=howto+left+button](http://www.ubuntuforums.org/showthread.php?t=219894&highlight=howto+left+button)

---

### Post by jimrz on 2006-10-02
> **eighthate said:**
> hEY I presently have a microsoft Mouse with lots of buttons including a Back and forward button on it, i wanted to know if there was a way to configure them since my mouse's buttons (back and forward) are presently detected as normal clicks( left click and right click)

Thanks :D

what MS mouse do you have and how many buttons? mine is a PS2 five button Intelli-Mouse. here is the appropriate section from my /etc/X11/xorg.conf that allows mine (including forward/back side buttons) to work properly:
```
Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ButtonMapping" "1 2 3 6 7"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
  EndSection
```

mine does not have side scrolling with the wheel, just left/right/wheel/forward/back. if yours is the same this should work for you. if yours has more buttons there will be some additions and one thing ("Buttons") needing change.

EDIT: if you do use this make sure to backup your current xorg.conf BEFORE you edit. do this
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

---

