---
title: "asus sabertooth z77 i5 3570k graphics problem"
date: 2012-06-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tiagalho on 2012-06-17
I can't get in to ubuntu 12.04, graphics are all choppy and the computer hangs at the login screen (when I can see it). tried usb, windows installer and cd installer. using a live cd it hangs at the ubuntu logo screen.
may be due to integrated graphics on the motherboard.

any help is appreciated.

---

### Post by tiagalho on 2012-06-19
no one?

---

### Post by kintoandar on 2012-06-21
Do you only use the onboard graphics card, have you tried with an external card?
Have you tried updating the kernel? -> [http://www.youtube.com/watch?v=traegZveTKo](http://www.youtube.com/watch?v=traegZveTKo)

Is all the remaining motherboard hardware correctly detected and working, sound, ethernet, etc?


[[]]

---

### Post by tiagalho on 2012-06-22
> **kintoandar said:**
> Do you only use the onboard graphics card, have you tried with an external card?
Have you tried updating the kernel? -> [http://www.youtube.com/watch?v=traegZveTKo](http://www.youtube.com/watch?v=traegZveTKo)

Is all the remaining motherboard hardware correctly detected and working, sound, ethernet, etc?


[[]]

I use an external graphics card. and I can't even get inside ubuntu... so I can't update the kernel :(

---

### Post by kintoandar on 2012-06-23
But did you actually installed ubuntu?
If so you may try:
- Disable the onboard graphics card
- Login using console mode, instead logging in graphic mode: ctrl+alt+F1 (on the login screen)
- Update the kernel on console mode

---

### Post by tiagalho on 2012-06-23
Ok I managed to install ubuntu and get inside :). Now I have a problem with dual monitors. :) but the rest is okay :)

---

### Post by kintoandar on 2012-06-23
Cool, glad to ear that!

Have fun ;)

---

### Post by tiagalho on 2012-06-24
I'm using a gts250 nvidia graphics card. but I cant seem to configure a dual monitor station. xorg.conf doesn't seem to save my configurations

---

