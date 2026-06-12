---
title: "Changing two keys"
date: 2009-01-11
forum: Apple Hardware Users
---

### Post by RobSoko315 on 2009-01-11
Hi,

I'm running Ubuntu on my MacBook Pro.  Upon installation I chose the "USA - Macintosh" Keymap.  This works fine, but I find the Command key much easier to reach when doing keyboard short cuts.  Is there a way I can switch command and control, so say I press (cmd + c) the computer will think I hit (ctrl + c)?  Likewise, I'd want to replace the control key for the command key.

Thanks, 

-Rob.

---

### Post by neoAnderson on 2009-01-11
On a PC keyboard, I would use "xmodmap", as in

xmodmap -e "keysym Pause = period"

would make the Pause key work as the period(.) for example. So you can swap anything. But for a Mac keyboard, I do not know if there is a keysym code available. You might do a search along these lines.

---

### Post by RobSoko315 on 2009-01-11
K, I'll see what I can get, thanks.

---

