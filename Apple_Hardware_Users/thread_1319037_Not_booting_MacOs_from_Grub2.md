---
title: "Not booting MacOs from Grub2"
date: 2009-11-08
forum: Apple Hardware Users
---

### Post by zatix on 2009-11-08
I have just installed ubuntu in my new macbookpro 5.5 and when I try to boot my leopard it says:

```
panic(cpu 0 caller 0x2ac8d5): "Incompatible boot args version 1 revision 4\n"0/SourceCaches/xnu/xnu-1456.1.25/osfmk/i386/AT386/nodul_dmp.c:542
```
I found it very strange, any idea?

---

### Post by linuxopjemac on 2009-11-08
You have to install rEFIt from OSX and boot from the rEFIt menu. Boot with option key pressed. You can then select Leopard or Linux.

---

### Post by zatix on 2009-11-13
> **linuxopjemac said:**
> You have to install rEFIt from OSX and boot from the rEFIt menu. Boot with option key pressed. You can then select Leopard or Linux.
Yea, I am willing to do that but I have to install it from my MacOs system. However, I can't boot it(just my ubuntu boots) so I was wondering if there is any image to burn in a usb drive or something like this to boot my Leoapard.


Thanks!

---

### Post by linuxopjemac on 2009-11-13
boot with option key pressed (the one with alt on the left). You can then choose Leopard or Linux...

---

