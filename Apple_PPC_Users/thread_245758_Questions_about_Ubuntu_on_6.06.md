---
title: "Questions about Ubuntu on 6.06"
date: 2006-08-28
forum: Apple PPC Users
---

### Post by railto on 2006-08-28
Hi there, i have recently installed ubuntu 6.06 on my 12" iBook G4 and until 10 mins ago was gonna wipe it off cause the mouse was so slow, but i found the post with the details to enable it properly, thanks to whoever posted that.  I have a few more questions.

First, i dont know how to conect to the wireless and kind of need it as i connect to my home and work networks using wireless.

Second, how do i map keys so that i can emulate right click

Last (i think) how do u use the bluetooth

Thanks in advance for your help

Mark

---

### Post by hajk on 2006-08-29
> **railto said:**
> 
Second, how do i map keys so that i can emulate right click
Mark

The man-page for xmodmap is your friend here, and so is the xev programme.
You also need the xkbset package installed.

In my case I wanted to use the lower Enter-key (next to the right Apple-key) as the right mouse click:

1. Running xev in a terminal, and hitting the lower Enter key showed that it had keycode 108.

After quitting xev, the following commands (without the prompts) in a terminal will do the trick:

$ xmodmap -e "keycode 108 = Pointer_Button3"
$ xkbset -m

It is best to put these commands in an executable script that can be run automatically at start-up time, so

$ sudo nano -w /usr/local/bin/keyboard

with the following contents

#!/bin/bash
# Keyboard mappings to be run at start-up

# Right mouse click
xmodmap -e "keycode 108 = Pointer_Button3"
xkbset -m

then make this file executable with 

$ sudo chmod +x /usr/local/bin/keyboard

Next, open the System-Preferences-Sessions menu, and add /usr/local/bin/keyboard to the start-up programmes.

I'm also running Ubuntu in a Parallels VM, and there the lower Enter key cannot be used that way. So, I added the right mouse click to the PageDown key as a second-level (with Shift) functionality. Trying xev showed that this was keycode 104, so the xmodmap line then becomes

xmodmap -e "keycode 104 = Down Pointer_Button3"

(again to be followed by xkbset -m).

Hope it'll work for you.

---

