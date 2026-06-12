---
title: "would this work  to install ubuntu on my imac"
date: 2007-06-25
forum: Apple PPC Users
---

### Post by zach12 on 2007-06-25
hi this was on the gentoo linux website
i love ubuntu but the way to install it on my imac was way(have had ubuntu on my laptop for for 50 weeks now so not have installed ubuntu a lot)hard if this works that would good 

I have an early NewWorld Mac such as the Blue and White G3. It should be compatible with the InstallCD, but on boot it returns an "Unknown or corrupt filesystem" error.

As a workaround, boot into Open Firmware by holding down the Apple + Option + O + F keys on startup. When the prompt appears, type:

Code Listing 2.2: Early NewWorld Mac Open Firmware work around

boot cd:,\\yaboot

The CD should boot as expected now, thanks to John Plesmid for this workaround. 
thanks

---

### Post by pxwpxw on 2007-06-25
I dont understand the question, but you could try
```

boot cd:,\install\yaboot

```
if thats the problem.

But if you have an iMac, you should not need to do that.

---

### Post by aantn on 2007-06-27
Could you repeat the question a bit more clearly?

---

### Post by zach12 on 2007-06-27
i'm trying to install ubuntu on my imac(not sure if it's a oldworld or newworld got it free)
i can't boot it from cd

---

### Post by pxwpxw on 2007-06-28
So what CD did you try?

---

### Post by zach12 on 2007-06-28
a ppc cd from freegeek

---

### Post by pxwpxw on 2007-06-29
Have you got an original imac  or a later model or what is it?

Are you using the c (not C) key to boot cd?

From macos, can you open the cd and what files can you see?

---

### Post by zach12 on 2007-06-29
i think it's a newer model

---

### Post by pxwpxw on 2007-07-02
My Apple info says that the newer iMacG3 has firewire ports as well as usb.
if it is the newer iMac try holding the Option Key while starting up with the CD in the drive, see what happens.

---

