---
title: "Control CRT via command line on an imac g3"
date: 2011-03-20
forum: Apple Hardware Users
---

### Post by rockhopper on 2011-03-20
I have forgotten how to turn the display on/off via command-line on an imac g3. Does anyone know how this can be done?

(Google brings up lots of results which use "xset dpms ..", but this does not really apply to me since I don't usually run X).

---

### Post by bd1308 on 2011-03-20
So you're usually using the Console? If thats the case, the screen blanker should kick in and at least prevent burn-in. But I think you're looking to turn off the whole tube, which should be trivial these days. I wonder if something like the PMU kernel module isnt loading, and thats the reason you're not able to have the screen automatically turn off

---

### Post by rockhopper on 2011-03-20
> **bd1308 said:**
> So you're usually using the Console? If thats the case, the screen blanker should kick in and at least prevent burn-in. But I think you're looking to turn off the whole tube, which should be trivial these days. I wonder if something like the PMU kernel module isnt loading, and thats the reason you're not able to have the screen automatically turn off


The screen does turn off automatically after a while. It also wakes up after I press a few keys on the keyboard.

However, I want to manually turn it off and on. (It automatically sleeps only after a long time, say 15 minutes or so. More importantly, I'm lazy and it's much easier to ssh and turn on a screen instead of walking across the room and pressing a few keys  on the attached keyboard to wake it:p)

I know that there is a particular command which does this; I used to use it a while ago. It was as easy as "sudo <command-name> on" and "sudo <command-name> off" or something similar.

---

### Post by bd1308 on 2011-03-20
sleep 1 && xset dpms force off|on

or 

xset dpms force off 
 or this....
Hi all,

I solved this a little differently, since I did not want the display to activate again when pressing a key or touching the mousepad.

I associated each of the following comands with a glaobal hotkey:

Key-Binding1: xrandr --output LVDS1 --off
Key-Binding2: xrandr --auto

where "LVDS1" is the name off the display you want to turn off (use "xrandr -q" too see which one to use).
If you have more than on display or some other fancy configuration the "xrandr --auto" may give you some weird results. But it works for me.

So now when I press the first hotkey the display is turned off but I can still use all input devices without activating the display again.
Except of course when I press the second hotkey, and everything magically reappears ;)

---

### Post by rockhopper on 2011-03-20
But, as I said in the opening post, these solutions require that X be running: something which isn't true in my case.

---

