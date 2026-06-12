---
title: "Booting straight into windows"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Striker9 on 2007-01-13
**Thanks for the help guys, your program worked perfectly Tomosaur.**

I currently have windows xp on my internal hard drive and ubuntu on an external usb drive. I would like to have windows boot normally without going to the boot selection screen (I guess this would be the GRUB loader) and instead press a key combination to go into linux. If I use "fixmbr" and restore window's boot loader will I still be able to get onto the linux drive?

---

### Post by riven0 on 2007-01-13
As far as I know, fixmbr will overwrite the GRUB, preventing you from getting into Linux. However, if Linux is on an external hd, there should be a way to boot up directly to it through the motherboard. So you may not need GRUB. 

On my motherboard I'm able to choose what device I want to boot from by hitting the F11 key. You, however, may actually have to go through your BIOS. It depends. I would check that out first. 

Otherwise, try changing the boot order in GRUB. Put your Windows entry before the Ubuntu entries and see if that makes a difference.

---

### Post by Striker9 on 2007-01-13
By pressing F12 I can select which drive I would like to boot from. That's what I was hoping to get to work. Is it easy to replace the GRUB if it ends up not working?

---

### Post by Tomosaur on 2007-01-13
Rather than going out of your way to do this, you can just change the behaviour of grub so that it boots Windows by default, and is not visible until you press Esc. You can also reduce the time it waits. All of this can be done by editing the file /boot/grub/menu.lst. It is self-commented, so it's pretty self-explanatory once it's opened.

Alternatively, check the link in my sig.

---

