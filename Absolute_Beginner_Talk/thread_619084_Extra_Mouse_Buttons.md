---
title: "Extra Mouse Buttons"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-21
Hi, I'm using a gaming mouse, and it's got a whole whack of extra buttons. is there a way to define these buttons?

For example, in the compiz manager, i want to have some effects done when i press, lets say, button 4.  As it stands right now, i dont have such thing as a button 4, although i do have more than enough buttons on the physical mouse to allow for a button 4.  Can i set one of these buttons as button 4?

---

### Post by 1/0 on 2007-11-21
Well, I've got this for my Razor Diamondback in xorg (You'll have to change it for your mouse - remember Google is a friend for this):

```

Section "InputDevice"
    Identifier   "Configured Mouse"
    Driver       "mouse"
    Option      "CorePointer"
    Option      "Resolution" "1800"
    Option      "Buttons" "9"
    Option      "Device" "/dev/input/mice"
    Option      "Name" "Razer Diamondback Optical Mouse"
    Option      "Protocol" "ExplorerPS/2"
    Option      "ZAxisMapping" "4 5"
    Option      "ButtonMapping" "1 2 3 6 7 8 9"
    Option      "one page back" "4"
    Option      "one page forward" "5"
    Option      "Emulate3Buttons" "true"
EndSection

```

I also had to do:

```
sudo xmodmap -e "pointer = 1 2 3 6 7 4 5"
```

In order to do the above automatically, you can add the above to (except sudo) to /etc/X11/xinit/xinitrc

---

### Post by Ck.asdf on 2008-01-29
Hello, I have a similar problem.
I tried following your instructions, along with a few attempted modifications in the numbers you provided in your example.  However, I got weird happenings, such as the mouse wheel going back/forward in Firefox history, not working at all, and I even made the side buttons (8 & 9) skip up and down the page like the up/down arrow keys on the keyboard.  None of this is what I wanted, though.
Perhaps you can help me;

1 = left click
2 = middle (scroll wheel) click
3 = right click
4 = scroll up
5 = scroll down
6&7 = not used
8 = "back" button
9 = "forward" button

back & forward reference Internet browsers as well as file browsers

I would like for 8 & 9 at the least to be able to go back & forth in Firefox, and even more than that, go back and forth within file browsers if possible.

Though 8 & 9 are numbers used, the mouse only has 7 buttons (counting up/down scrolling).

suggestions? thankS!

a bit of code ...
```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
EndSection
```

(Emulate3Buttons needs to be no, as I find it infuriating when I click both buttons, that middle-click is enabled, though I suppose it'd have a use for laptops.)

---

