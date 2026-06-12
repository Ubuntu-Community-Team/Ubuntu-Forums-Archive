---
title: "disable mouse buttons"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by pataphysician on 2006-06-20
hi. just did a fresh install of dapper, was using hoary until now.

i have a wireless usb logitech mouse. the wheel can be depressed or moved left or right. i'd like all three of these actions to just count as a middle-click -- i don't want the back/forward functionality. it worked like this under hoary by default (i guess the left/right clicks just didn't work). i think this is the relevant part of xorg.conf:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
#     Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

i tried commenting out the ZAxis line, but that didn't work. how can i disable or re-map the 4th and 5th buttons?

---

### Post by pataphysician on 2006-06-21
bump...

i used xev to check the mouse buttons. buttons 4 and 5 are the up/down wheel, buttons 8 and 9 are left and right wheel motions. those are what i want disabled. so i tried adding the line

        Option          "Buttons"               "5"

to xorg.conf, thnking that it would ignore anything higher than that, but that didn't work.

i know this is insignificant, but it's driving me crazy. anyone have any ideas? (other than buy another mouse -- i would, but this one is perfect for my needs, save the annoying extra buttons.)

---

