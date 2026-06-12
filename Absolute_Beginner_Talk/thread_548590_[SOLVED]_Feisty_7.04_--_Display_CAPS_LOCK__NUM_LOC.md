---
title: "[SOLVED] Feisty 7.04 -- Display CAPS LOCK / NUM LOCK status?  And...?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-09-11
I'm in the process of upgrading from Dapper (6.06) to Feisty (7.04).

Under Dapper, I had a little panel gadget that visually displayed the status of my (Logitech wireless) keyboard's CAPS LOCK, NUM LOCK, and SCROLL LOCK keys.  I can't find an equivalent for Feisty.  Does anyone know where I might find such a thing?

Also, is anyone aware of a user-friendly, non-programmer way to require that the CAPS LOCK key be pressed and held for, say, two seconds or so before becoming applied?  There are some third-party gadgets for Windows that do this but I can't seem to find anything for Linux / Ubuntu...

Cheers & thanks,
Ric
SFO

---

### Post by MattJ100 on 2007-09-12
There is an applet called lock-keys-applet. You will find it in synaptic, or by typing in Terminal: sudo apt-get install lock-keys-applet

About the 2 second delay... my solution was to map Caps Lock to be Ctrl. I can't say I have missed it once :)

You can do this in System->Preferences->Keyboard->Layout Options
Ctrl key position->Make CapsLock an additional Ctrl

Hope this helps.

---

### Post by Phrawm48 on 2007-09-12
Yes -- *lock-keys-applet* was exactly what I was looking for.  Thanks for helping me find it!

I'm gonna' poke around at the reassignment of CAPS LOCK a bit later.

Cheers and thanks 'gain,
Ric
SFO

---

### Post by Catz3705 on 2008-03-25
> **MattJ100 said:**
> There is an applet called lock-keys-applet. You will find it in synaptic, or by typing in Terminal: sudo apt-get install lock-keys-applet

About the 2 second delay... my solution was to map Caps Lock to be Ctrl. I can't say I have missed it once :)

You can do this in System->Preferences->Keyboard->Layout Options
Ctrl key position->Make CapsLock an additional Ctrl

Hope this helps.

Needed help with Caps Lock display on Logitech Cordless Optical Black keyboard. Searched and found your post. Installed lock-keys-applet and solved most of the keyboard problem. Now have panel dislay of Caps Lock and Num Lock Keys. Applet configuration shows check off box for Scroll Lock, but it appears to have no effect for this keyboard type.

Thanks for posting your solution.

-met

---

### Post by Phrawm48 on 2008-03-25
[I]Applet configuration shows check off box for Scroll Lock, but it appears to have no effect for this keyboard type.
[/I]
Yeah, I have the same problem but insofar as I seldom activate Scroll Lock even accidentally, I just learned to live with it.

Cheers,
Ric
SFO

---

