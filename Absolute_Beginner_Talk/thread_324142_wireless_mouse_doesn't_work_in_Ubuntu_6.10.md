---
title: "wireless mouse doesn't work in Ubuntu 6.10"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by fartsack on 2006-12-23
Hi all,

I managed to successfully install Ubuntu on my PC, all the while using a Logitech MX700 wireless mouse without issues.  Now after rebooting Ubuntu, I can get to the login screen but now my mouse doesn't work.  So, in essence I get to the login screen, but can only work from my keyboard.  :confused: 

Of course, the mouse still works when I boot to Win XP.

Thanks in advance 

/fartsack

---

### Post by gborzi on 2006-12-23
I have the same mouse, MX700, along with an MX3000 wireless keyboard, and it has worked and still works without any problem (well, the only problem is when the batteries get depleted). This is the section in my xorg.conf for this mouse:
> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
Hope this helps.

---

### Post by fartsack on 2006-12-23
thanks - I'll try updating my xorg.conf to match yours.  My only question now is when I'm at the login screen, what's the quickest/easiest way to bring up a terminal session without having a mouse to guide me ?


/fartsack

---

### Post by _simon_ on 2006-12-23
I also have an MX700 but my Xorg is slightly different:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Dev Name" "Logitech USB Receiver"
    Option         "Dev Phys" "0000:00:02.0-1/input0"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "10"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7 "
    Option         "Resolution" "800"
EndSection

```

Not sure how you get a terminal from the login screen. 

When grub loads and it gives the countdown, press ESCAPE and choose SINGLE USER MODE.

Then when it's finished loading all you need to do is:
```

sudo nano /etc/X11/xorg.conf

```

---

### Post by gborzi on 2006-12-23
> **fartsack said:**
> thanks - I'll try updating my xorg.conf to match yours.  My only question now is when I'm at the login screen, what's the quickest/easiest way to bring up a terminal session without having a mouse to guide me ?

If you mean that you want to open a terminal inside X, e.g. gnome-terminal, press <Alt>F1 to open the gnome menu, navigate with the arrows keys to Accessories->Terminal and press Enter.

---

