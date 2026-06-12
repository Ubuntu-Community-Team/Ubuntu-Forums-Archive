---
title: "using joystick"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-04
I need to use my joystick for pcsx emulator. The emulator wants me to specify a file /dev/joy1 for a joystick device. I have a joystick, i plugged it in, should i do something more in order for this file to appear ?
Maybe some kind of terminal command ?

Or if this is too complicated can you tell me where is the dev file for keyboard located ?

---

### Post by Sasa_Ivanovic on 2007-01-04
I searched the whole file system for anything containg "joy" and no results. Also i searched for "keyboard" in /dev no results either ....

Has anyone used joystick in Ubuntu at all ?

---

### Post by luvinit on 2007-01-04
I don't know anything about this, but I think it is more likely to be located in dev/input/js0

---

### Post by Duncan_Idaho on 2007-03-22
I'd like to use my usb joypad too
I use PCSX-df and I got the same error as OP
but there is no js0 in any directory under /dev

---

### Post by yabbadabbadont on 2007-03-22
Plug in the usb device then, in a terminal, run "dmesg".  Look at the output at the bottom for any mention of the device.  Post that output back here.

---

### Post by Duncan_Idaho on 2007-03-22
well, you have help me in an unexpected way, I runned that command, but in the output my joypad wasn't mentioned, so I crawl behind the desk to check the cables and thanks to you I realized that my joypad was unplugged xD :lolflag: 
so I plugged and it works perfectly, so thank you :)

---

