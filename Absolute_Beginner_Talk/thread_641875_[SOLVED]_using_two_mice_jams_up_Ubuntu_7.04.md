---
title: "[SOLVED] using two mice jams up Ubuntu 7.04"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-12-15
I have a 1999 gateway laptop with a touchpad. It has a dual boot Win98/Ubuntu 7.04. Sometimes I need to plug in a second mouse (USB) so that I colleague of mine can also point out things on the screen when we are working together. When I am in Win98, there is no problem. The computer accepts messages from the touchpad as well as from the USB mouse very smoothly with no hitches. But when I am in Ubuntu working in OO, with the USB mouse plugged in, the computer is constantly taking very long pauses especially just after the USB mouse is used to point something out, and when I then try to use the touchpad mouse. We end up having to wait constantly for the computer. Feisty is clearly not managing well with the two mice. Is there any way to fix this problem so that both mice can be used smoothly as happens in Win98?

Thanks!

---

### Post by linuxisfree on 2007-12-16
> **swarup said:**
> I have a 1999 gateway laptop with a touchpad. It has a dual boot Win98/Ubuntu 7.04. Sometimes I need to plug in a second mouse (USB) so that I colleague of mine can also point out things on the screen when we are working together. When I am in Win98, there is no problem. The computer accepts messages from the touchpad as well as from the USB mouse very smoothly with no hitches. But when I am in Ubuntu working in OO, with the USB mouse plugged in, the computer is constantly taking very long pauses especially just after the USB mouse is used to point something out, and when I then try to use the touchpad mouse. We end up having to wait constantly for the computer. Feisty is clearly not managing well with the two mice. Is there any way to fix this problem so that both mice can be used smoothly as happens in Win98?

Thanks!

Now, i'm not entirely sure about this... but maybe you can try to check the settings in System --> Preferences --> Mouse (If its there). I hope THAT would help...

Not entirely sure about this, but i hope something there helps:)

---

### Post by tgalati4 on 2007-12-16
You might have to set up both mice in xorg.conf.  Search the forums for some ideas.  Also check the BIOS for an option for legacy USB keyboard support.  This will control the USB interrupts at the hardware level as opposed to software which could be slower.

---

### Post by swarup on 2007-12-16
> **tgalati4 said:**
> You might have to set up both mice in xorg.conf.  Search the forums for some ideas.  Also check the BIOS for an option for legacy USB keyboard support.  This will control the USB interrupts at the hardware level as opposed to software which could be slower.

I'm pretty sure both mice are set up in xorg.conf, because when I first loaded Feisty in my computer 7 months ago, the touchpad wasn't working properly. Ultimately I found that while there WAS a setup for a usb mouse in xorg.conf, there wasn't anything there for the touchpad. So with the help of this forum, I was able to add that, so the touchpad works fine. I'd like to go back to xorg.conf just to confirm that the usb mouse setup is indeed there, but I forget how to open xorg.conf. Could somone remind me?

Also, because I believe there is a setup for both mice in xorg.conf, I wonder whether anyone has any further suggestion. (In the mean time I will look in the bios for legacy USB keyboard support as suggested above. As this is a 1999 laptop, ie sort of old, there may not be any such thing. But I will check.)

---

### Post by swarup on 2007-12-16
> **tgalati4 said:**
> You might have to set up both mice in xorg.conf.  Search the forums for some ideas.  Also check the BIOS for an option for legacy USB keyboard support.  This will control the USB interrupts at the hardware level as opposed to software which could be slower.

Your suggestion was right on the mark. I found the solution in the BIOS. In the BIOS there were two settings which I changed. One was to enable USB keyboard support, and the other was to change the setting for PS/2 apparatus from "exlusively" internal, to "simultaneous" meaning it would allow the simultaneous use of internal and external PS/2 apparatuses. I don't know which if these two changes did the trick, but now both the internal touchpad and the external USB mouse are working fine together, with no long pauses or anything. It is working perfectly. Thank you!

---

