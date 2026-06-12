---
title: "GRUB &amp; USB Keyboard"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by ConcreteDonkey on 2007-12-24
Hello everyone,

I have just recently installed Ubuntu on my ol compute, everything went fine except I can't use my wireless USB keyboard with GRUB. I have enabled USB Legacy Support in the BIOS but I'm still not getting anything :(. I'm wondering if there is anyway to make it work or if I will just have to buy a wireless keyboard that includes a PS/2 connector?

---

### Post by Duck2006 on 2007-12-24
You may need the PS/2 Keyboard as it hasn't loaded the usb drivers at grub boot time.

---

### Post by ConcreteDonkey on 2007-12-24
Thanks, Although I was wishing you wouldn't say that :)

---

### Post by deoray on 2007-12-26
I recently faced same problem with Grub after installing new USB corded keyboard.

Keyboard used to work fine with BIOS, Windows 2k and ubuntu graphic mode but not with GRUB menu. I enabled support for USB keyboard from one of the BIOS option and it started working with GRUB as well.

Lookup BIOS and see if you find option for USB keyboard support and hopefully that will solve problem.

---

### Post by kellemes on 2007-12-26
> **deoray said:**
> Lookup BIOS and see if you find option for USB keyboard support and hopefully that will solve problem.

This is the way indeed if.. mb supports it.. I'm in bad luck.. can only use PS2 since the newer USB2-keyboards are not supported by my mb. So it won't work until the OS takes over..

---

### Post by yaknowwat on 2007-12-26
sometimes with BIOS they have a double check for USB things check around for that one is to allow USB support the next is to enable it.

---

### Post by ConcreteDonkey on 2007-12-27
Thanks for the help, although I have tried all of the settings in the BIOS none of them seemed to work. So I just bought a wireless keyboard with a PS/2 adapter :)

---

