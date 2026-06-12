---
title: "Using any USB device causes Linux Ubuntu to either crash or slowdown to a crisp"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by user_of_gnomes on 2006-02-12
Hello, Folks.

Sorry to disturb you again so soon but I am facing an, in my eyes, very frustrating problem: 

Whenever I connect an USB device and turn off/restart the computer Linux takes ages to load and once it has succesfully loaded, it will slow down immensly. Or crash. 

This behaviour has occured both with my newly acquired Belkin KVM switch, which relies on an USB port for keyboard/mouse input and an USB mouse which I normally use an USB to PS/2 converter for. The converter works fine, but when I plug in the mouse or KVM switch, fire starts falling from the sky. It becomes fire and brimstone when I connect my FHD2-Pro (Fat32) external HDD, then Linux just crashes or refuses to boot. 

If I plug in the mouse AFTER Linux has booted, it works like it should. 

But if I reset, I get a strange error right after the point where it synchronizes with a timeserver. It says something about "Not bothering" then "Try booting with irqpoll" (I swear I am going to kick it next time it decides to argue with me, bloody machine) and then it says "dropped IRQ 5 (or 11, in case of the KVM switch) It also lists my VIA-RHINE network adaptor. 

Well that's actually all there is to the error, there's some numbers probably in hexadecimal and a few names in the USB sentence that say usb_core and usb_ncd_irq or something in that manner. 

The BIOS is properly configured, it's even more fine tuned than when I had Windows XP installed. Which worked fine in the USB department.

---

