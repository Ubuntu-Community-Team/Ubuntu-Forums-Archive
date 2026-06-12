---
title: "minimal working kernel config"
date: 2008-10-17
forum: Apple Hardware Users
---

### Post by DodoFXP on 2008-10-17
Hi everyone

I was wondering if MacBook Pro 4.1 users could post their kernel config?
I am trying to get me a minimal kernel but the last two didnt boot :(

Thanks

DodoFXP

---

### Post by DodoFXP on 2008-10-18
bump. No one?

---

### Post by volanin on 2008-10-18
I have a Macbook 2.1, so my config will be quite useless to you.
But I have some advice (and guess what: it's for free!)

When building your own _minimal_ kernel, there are three things to consider:
- The essential kernel components
- The hardware support
- The software support.

Making a minimal kernel, then, is quite subjective.
I might disable Firewire for example, but you might need it.

So, besides the essential kernel components like the *IO Scheduler and the TCP/IP stack*, you must also decide on what parts of your macbook hardware you want to support, such as *Watchdog Timer and Bluetooth*, and decide on what software you want to support, such as *IPTables and PPP conection, not to mention the filesystem support such as EXT2/3 and FAT!*

To be honest with you, the _really minimal_ kernel config would probably boot with no graphic interface support besides VESA, no sound at all, no internet card support, no nothing! It would be quite useless except for a very specific embedded project.

---

