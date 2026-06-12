---
title: "Please help! MX700"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-04-07
This is really bugging me now and I believe I have tried everything suggested in the main thread about MX mice.

What Works:

Left & Right buttons
Scroll wheel up & down
Back & Forward thumb buttons
Cruise Down (all be it at the same speed as the scroll wheel?)

What doesn't work:
Cruise up - it is also acting as page forward!
Program button - I never use this and don't care about it.

So...

I'd REALLY like to know how I get cruise up to act as it should and how I configure both cruise up and cruise down to scroll FASTER than the scroll wheel or simply set them to page up / page down!

Not sure what is needed but here is my Xorg.conf:

```

Section                 "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Protocol" "ExplorerPS/2"
        Option          "Dev Name" "Logitech USB Receiver"
        Option          "Dev Phys" "0000:00:02.0-1/input0"
        Option          "Device" "/dev/input/mice"
	Option          "Buttons" "7"
        Option          "ZAxisMapping" "6 7"
        Option          "Emulate3Buttons"       "no"

EndSection

```

I also have an Xmodmap:

```

pointer = 1 2 3 6 7 4 5

```

(I needed the Xmodmap in order to make cruise down work it seems)

---

### Post by _simon_ on 2006-04-08
Anyone? :(

---

### Post by Sabar on 2007-04-02
I Just did this

[Logitech Mx700]("http://www.ubuntuforums.org/showthread.php?t=399374")

Sabar

---

