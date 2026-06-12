---
title: "Send the Apple Command key with a normal keyboard?"
date: 2009-09-14
forum: Apple Hardware Users
---

### Post by scm007 on 2009-09-14
Hi, I am using one keyboard/mouse to power my Ubuntu machine and a Mac Mini using Synergy.

However I can't for the life of me figure out how to get this one keyboard to send the Apple command key!

Thanks.

---

### Post by _mario_ on 2009-09-15
> **scm007 said:**
> Hi, I am using one keyboard/mouse to power my Ubuntu machine and a Mac Mini using Synergy.

However I can't for the life of me figure out how to get this one keyboard to send the Apple command key!

Thanks.

well, i don't really understand your problem. but i think, i'm somewhat experienced with keyboards.

sending the Apple command key with a normal keyboard, is simple: according to the USB HID (human interface devices) specification, does the Apple command key emit exactly the same keycode as the Windows key on standard keyboards. if you use xev to dump all X11 key events, you'll see that the Apple command key and the Windows key are indeed assigned the same X11 keysyms (Super_L/Super_R).

hence, just press the Windows key.

ciao,
Mario

---

### Post by scm007 on 2009-09-15
I tried that, it doesn't work.

NVM. Figured it out, left ALT did it.

---

