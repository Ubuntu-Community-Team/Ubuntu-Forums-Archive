---
title: "usb flah permissions"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-03-18
Hi all 

the flash drive has gon and given itself a permission ,,,has been fine  plugged it in Just now all files locked and I cant read orr write to it 

tried this  from reading past post and wiki 

if its ext3 do the following:
1. Open a terminal
2. Type "sudo chown [your username] /media/nameoftheusbdrive". Press enter
3. Type "sudo chgrp [your username] /media/nameoftheusbdrive". Press enter again.

but  comes back invalid user ,,, 

How do I change the permissions for USBs  permanantly !!!,

Kind regards Stephen

---

### Post by gilgongo on 2007-03-18
I'd love to know the resolution to this one was well. The answer always comes in the form of chmoding manually - but why? Why aren't all devices simply mounted as the user that needs them? If a malicious process accesses my USB device, how is that any worse than it accessing my local filesystem or network drives? Hell, I can't event delete photos off my camera using Ubuntu. This has to be wrong for a desktop OS, no?

---

### Post by basilwatson on 2007-03-18
Completely agree , though others desktop dont do it from memory ,,,so why Ubuntu 

So its change mod???

Stephen  ( quicker to reboot into window and boot back !!!!! )

---

