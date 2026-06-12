---
title: "Mouse Wheel"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by ncr on 2007-09-06
After using DOS, WINDOWS, and OS/400 for 10 years I've made the transition to Linux (via Ubuntu). I've only been using it for a couple days and don't quite understand the file system yet or the BASH command line interpreter. 

My (first) problem that I'm looking for help with is my Microsoft PS/2 mouse wheel between the left and right button. It doesn't function whatsoever in Ubuntu (also both the left and right mouse buttons work fine). I'd like to be able to scroll using the wheel. 

Does anyone have any easy to follow steps for making this work with Ubuntu 6.06?

Any feedback is much appreciated. 

Thanks,
Nick

---

### Post by greybirds on 2007-09-06
Try this. Go to your main menu: Applications > Accessories > Text Editor. This will open gedit, a text file editor. 

In the text editor's window, select File > Open and type the following into the Location field:
[INDENT]/etc/X11/xorg.conf[/INDENT]
and press the Open button. Notice the X in "X11" is capitalized. That's important. This will open the configuration file for your graphics, keyboard, and mouse.

In the file, scroll down until you see the section for your mouse (you can also use the menu Search > Find and type in "mouse"). 

Is there a line containing the words "ZAxisMapping" in the mouse section?

---

### Post by .exe on 2007-09-07
Ok, just installed Fiesty on my brand new laptop and I'm having the same issue. I tried reconfiguring  Xorg and picking something else for the mouse, but that didn't help. Heres my xorg info:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "GlidePointPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

---

