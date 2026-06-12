---
title: "vbox problem"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by veebee on 2007-07-24
I have to set up a virtual machine as my laptop (AMD Turion 64X2) running kubuntu 64 bit is not paired with any other machnes to validate work done.

I have setup/ installed vbox, and all seems great until I go to install kubuntu 64bit on the vm iget the message :

"your cpu does not support long mode. Use a 32 bit distribution"

any ideas why?

Thx
VB

---

### Post by Al3xK3aton on 2007-07-24
The solution is to follow directions and use a 32 bit distribution.

---

### Post by starcraft.man on 2007-07-24
> **veebee said:**
> I have to set up a virtual machine as my laptop (AMD Turion 64X2) running kubuntu 64 bit is not paired with any other machnes to validate work done.

I have setup/ installed vbox, and all seems great until I go to install kubuntu 64bit on the vm iget the message :

"your cpu does not support long mode. Use a 32 bit distribution"

any ideas why?

Thx
VB

VBox only supports 32 bit guests now. I assume your host is 32 bit too else you'd have had problems installing VBox (I think at least). There really isn't any reason to need a 64 bit VM guest, I'd just download the 32 bit ISO and install that.

If you absolutely need the 64 bit verison, install VMware Server/Workstation.

---

