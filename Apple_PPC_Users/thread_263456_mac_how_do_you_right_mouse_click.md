---
title: "mac: how do you right mouse click?"
date: 2006-09-23
forum: Apple PPC Users
---

### Post by chule on 2006-09-23
hello
my first post, just getting into ubuntu
i've searched for this but got dozens of posts that didn't seem to have anything to do with it.
on a mac, which has no right mouse button, how do you simulate a right-mouse click? and for that matter how do you simulate a middle-mouse click?
thanks.....

---

### Post by didg on 2006-09-23
F11 (middle) and F12 (right) keys

---

### Post by DirtDawg on 2006-09-23
Does anyone know if there's a way to remap these keys? I would love the command(or "apple") key to act as a RMB.

I tried mouseemu, and although the alt=MMScroll works really well, it broke everything else (i.e. no RMB at all).

Anyways, is remapping possible?

I'm using Xubuntu Dapper

---

### Post by hajk on 2006-09-24
Remapping keys is certainly possible, the general command to remap a single key is

xmodmap -e "keycode xxx = KEYFUNCTION"

where xxx = 3-digit number of key to be remapped, and
      KEYFUNCTION = the particular function to be mapped to that key
                    (like Pointer_Button3 for the right mouse click).

You should also run the xkbset command to make these mappings stick, install the xkbset package if necessary.

How do you know these data? Run the xev command in a terminal (you may have to install the xev package first), then try various keys and note the current mappings.

I recommend collecting all these mapping commands in an executable file, to be  run at start-up. Refer to my notes (see sig) on installing Ubuntu on the HD of a MacBook for details on how to do this. (Note that the key mappings on an MBP are not necessarily the same as on the MB.)

---

### Post by DirtDawg on 2006-09-24
> **hajk said:**
> Remapping keys is certainly possible, the general command to remap a single key is

xmodmap -e "keycode xxx = KEYFUNCTION"

where xxx = 3-digit number of key to be remapped, and
      KEYFUNCTION = the particular function to be mapped to that key
                    (like Pointer_Button3 for the right mouse click).

You should also run the xkbset command to make these mappings stick, install the xkbset package if necessary.

How do you know these data? Run the xev command in a terminal (you may have to install the xev package first), then try various keys and note the current mappings.

I recommend collecting all these mapping commands in an executable file, to be  run at start-up. Refer to my notes (see sig) on installing Ubuntu on the HD of a MacBook for details on how to do this. (Note that the key mappings on an MBP are not necessarily the same as on the MB.)


I actually spent about two hours last night messing with the xmodmap command trying to get this to work, but I just could not figure out how to bind mouse functions to the keyset numbers. I tried "button 3", "3", "moue 3", etc, and xmodmap -pke does not show keycodes for mousebuttons.  In addition, I couldn't get any useful info from th "xev" command, like a name or keycode for pointer events.

  I finally figured out a way to gerrymander things and posted it [here]("http://www.ubuntuforums.org/showthread.php?t=264074"). But the method you posted here is better as I can use alt+command or cntrl+command, which would be preferable.
 
The real key here is "Pointer_Button3". That was the missing ingrediant I could just not find.
Thank you for the response.

---

