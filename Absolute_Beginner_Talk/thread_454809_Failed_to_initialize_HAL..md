---
title: "Failed to initialize HAL."
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by M4v3r1ck on 2007-05-25
When I boot up my computer and log in it gives me the error "Failed to initialize HAL."
For starters - I'm a Linux n00b. 

Secondly, this is a laptop. Compaq Presario V2000, running Ubuntu Edgy Eft.
Does anyone have an idea of what I need to do to get that fixed? I believe HAL is the hardware abstraction layer...

EDIT: Bump.

---

### Post by Tux Aubrey on 2007-05-26
I haven't got a definitive answer for you, but this used to happen to me a lot (with Dapper I think).

It usually involved an errant usb device at boot but I couldn't reproduce it consistently.

If your problem is recurring every boot, you could try reinstalling hal (do a search in synaptic and mark the hal package for reinstallation with the right mouse button).  That might fix it.

---

