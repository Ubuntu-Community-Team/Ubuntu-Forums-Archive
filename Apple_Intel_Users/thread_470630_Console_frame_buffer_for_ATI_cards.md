---
title: "Console frame buffer for ATI cards"
date: 2007-06-11
forum: Apple Intel Users
---

### Post by Muffa on 2007-06-11
Hi, I'm running Feisty 2.6.20-16-generic on MacBook Pro Core 2 Duo very fine, but I have also this question:
how can I set console frame buffer for the MacBook Pro lcd panel (1440x900) resolution?

I've tried some tricks like grub's menu lines or modeline xorg.conf's Monitor sections without success.

Does anyone have a solution?

Thanks in advance.

Cheers, Marco.

---

### Post by Muffa on 2007-06-12
Nobody? :(

---

### Post by cevans on 2007-06-13
I've had terrible trouble in the past trying to find console modelines for high resolutions. Search around on the internet for the modeline for 1440x900, and then use that with the vesa framebuffer.

---

### Post by Muffa on 2007-06-13
Thanks for reply.
Do you know the steps for apply your solution? I've googled around without success, or probably I'm too much noob to understand the solution! :D

Thanks a lot.

---

### Post by Hibbelharry on 2007-06-26
Hi !
I didn't try this on a macbook, but it should work.
First edit /etc/initramfs-tools/modules an add radeonfb to it. Then rebuild your initial ramdisk by doing update-initramfs -u -k all. Then add a parameter for your resolution to your kernel line in grub or whatever you use. append video=radeonfb:1440x900.

Since this mode is fairly uncommon up to now i'm not sure whether it is supported by radeonfb. 

Good Luck
Hibbelharry

---

