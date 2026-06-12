---
title: "Can't get Side Mouse Buttons Working Right"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by esc1 on 2007-06-06
I have an A4Tech mouse.  It has two side buttons I would like to use for forward and back in firefox and while viewing folders.  This mouse also has two scroll buttons.  One of them is clickable.

I have installed IMwheel but I can't get the config right.  

Tried my best to follow the guide here:  
[http://easylinux.info/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox](http://easylinux.info/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox)

Here is what I have in my /etc/X11/xorg.conf

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "6 7"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "9" 
    Option         "ButtonMapping" "1 2 3 4 5 8 9"

I added this to the end of /etc/X11/imwheel/imwheelrc

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right 

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right


Here is what I have for /home/login/mouse:

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

Right now my scroll is even borked taking me forward and backward.  My side buttons are scrolling up or down the page but one click at a time.  

To restate I would like to be able to go back and forward with the side buttons in Firefox and while browsing files and scroll again with the mouse wheel.  If anything cool can be done with the extra scroll or clickable scroll I'm all for that as well.  Being able to minimize all windows would be nice for the clickable scroll button.  Big thanks for any help. :)

---

### Post by whistle on 2007-06-06
I had that problem where the scroll wheel and the side buttons seemed to be switched around...

I changed```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "6 7"
Option "Emulate3Buttons" "true"
Option "Buttons" "9"
Option "ButtonMapping" "1 2 3 4 5 8 9"

```

into

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "**4 5**"
Option "Emulate3Buttons" "true"
Option "Buttons" "9"
Option "ButtonMapping" "1 2 3 **6 7** 8 9"

```

---

### Post by esc1 on 2007-06-06
That did it!  Thank you very much. :)

---

### Post by Ruined on 2007-07-10
> **whistle said:**
> I had that problem where the scroll wheel and the side buttons seemed to be switched around...

I changed```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "6 7"
Option "Emulate3Buttons" "true"
Option "Buttons" "9"
Option "ButtonMapping" "1 2 3 4 5 8 9"

```

into

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "**4 5**"
Option "Emulate3Buttons" "true"
Option "Buttons" "9"
Option "ButtonMapping" "1 2 3 **6 7** 8 9"

```

I actually had to do the exact opposite of you O_O

```

Option "ZAxisMapping" "**4 5**"
Option "ButtonMapping" "1 2 3 **6 7** 8 9"

```

to

```

Option "ZAxisMapping" "**6 7**"
Option "ButtonMapping" "1 2 3 **4 5** 8 9"

```

so, if it's not working one way, try the other.
Btw, this post helped me a ton in getting my mouse working ^^

---

