---
title: "xmodmap customization problems"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by furtivefelon on 2006-02-12
hello, recently i was trying to modify my keymaps to ease emacs control use by mapping control onto caps lock and viseversa

however, by following the guide within man xmodmap, it didn't work.. the guide is:

!
! Swap Caps_Lock and Control_L
!
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L

and my original xmodmap -pm output is:
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_R (0x71),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

My current xmodmap -pm output is:
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_R (0x71),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

I'm not sure how to revert back to original.. The first time around, the whole tutorial went flawlessly, then when i checked, nothing works.. So i tried to the tutorial again, as i type in xmodmap -e 'keysym Control_L = Caps_Lock', it give me the following error: 
xmodmap:  commandline:1:  bad keysym target keysym 'Control_L', no corresponding keycodes
xmodmap:  1 error encountered, aborting.

I have no idea what is wrong, and why it doesn't recognize Control_L, can someone help me out? Thanks alot!

---

### Post by furtivefelon on 2006-02-12
Ah, just fixed it, i realized that you can copy/save series of command into a file then do xmodmap filename.. After i did that, everything works fine.. I have no idea what happened...

---

