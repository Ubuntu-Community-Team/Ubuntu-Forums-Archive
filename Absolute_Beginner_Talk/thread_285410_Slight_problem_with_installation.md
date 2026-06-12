---
title: "Slight problem with installation"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Kha0sK1d on 2006-10-26
Hello,

I've read the "must read" links for beginners and haven't found a solution to my problem.

I am trying to install Ubuntu 6.06 (Dapper Drake?). The loading bar completes, but after that, I get this message that starts displaying every 2 seconds that eventually fills my screen:

[some numbers] hub 5-0:1.0: connect-debounce failed, port 4 disabled

After that displays a couple of times a Yes or No option comes up (I forgot what is said), but I couldn't choose anything regardless. I tried pressing escape and every button, but eventually pressed the power button and it went through an uninstallation process and everything is back to normal. Does anyone know what's wrong? Any help would be greatly appreciated.

---

### Post by bodhi.zazen on 2006-10-26
Try booting with the "noapic" option.

---

### Post by Kha0sK1d on 2006-10-26
Sorry, I'm not quite sure how to do that or what it is. Could you explain in more detail or direct me to somewhere that can? Thank you for the quick reply.

EDIT: I've found out it's a kernel option, but I still have no idea where I put that little snippet of code.

---

### Post by Kha0sK1d on 2006-10-27
Found out how to use it, tried, and failed. I tried a second time using "acpi=off noapic pci=bios pnpbios=off" as described by Klaus Knoppix to be the solver of most problems with Linux booting. It finally worked, but I could not input with the keyboard, so I decided to shut down an try again. Every attempt thereafter did not work and kept showing the same message I first wrote about. Please help me out! Thanks in advance.

---

