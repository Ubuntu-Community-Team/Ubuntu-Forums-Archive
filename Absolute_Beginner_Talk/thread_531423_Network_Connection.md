---
title: "Network Connection"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by tgarbarz on 2007-08-21
I just installed Ubuntu 6.10 and cannot get my network card to work.  I have a wireless NIC but I think there is an issue with the PCI slot.  However, there is an internal Hardwired NIC that should work but I do not know where to start trouble shoting etc...Any help would be appreciated.

---

### Post by tgarbarz on 2007-08-21
WOW, followed the "documentation" checked and un checked the box for wired connection and it worked!  Now does anyone know of a way to check the PCI slot to prove the wireless connection is hardware?

---

### Post by overdrank on 2007-08-21
> **tgarbarz said:**
> WOW, followed the "documentation" checked and un checked the box for wired connection and it worked!  Now does anyone know of a way to check the PCI slot to prove the wireless connection is hardware?

Hi if you can post the output of the command
```
lspci
``` 
In the terminal located under applications, accessories, terminal

---

