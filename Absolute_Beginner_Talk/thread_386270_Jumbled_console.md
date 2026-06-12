---
title: "Jumbled console"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by lookmanohands on 2007-03-16
When I was floating through different commands I read something about being able to go to your console and I was sure if I was doing it properly because when I do go to it my console just appears as a bunch of jumbled colored lines (not the terminal). I was just wondering if this is how its supposed to be or did Ubuntu install improperly?

---

### Post by Brent099 on 2007-03-20
I've been having the exact same problem (on two different ubuntu based installations).  have you found a solution?

I'm running on an acer aspire 5672wlmi (ATI x1600)

---

### Post by mcduck on 2007-03-20
I'm using Mobility Radeon X1600, and I solved the problem by adding vga=792 to kernel options in /boot/grub/menu.lst. That makes Ubuntu to use 1024x768 resolution with 32bit colors when booting & in console.

1. run 'gksudo gedit /boot/grub/menu.lst'
2. find the default options section and add vga=792 like I have here:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=792
```
3. Then the actual kernel option:
```
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro splash vga=792
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```
4. save the file, reboot, and hopefully console is now working for you :)

---

### Post by hilde on 2007-03-22
My younger brother's computer also has an ATI Radeon X1600 (unfortunately). I tried the "vga=792" solution. Now I don't get these colored lines anymore and I can login and type some commands, but when I try to go back to the graphical screen with Ctrl-Alt-F7, I get a black screen and the computer hangs, as it did when I got the ugly colors.

I didn't look for the "defoptions" part mentioned in your post, since I don't think changing something that has been commented out would make any difference.

---

### Post by mcduck on 2007-03-22
> **hilde said:**
> My younger brother's computer also has an ATI Radeon X1600 (unfortunately). I tried the "vga=792" solution. Now I don't get these colored lines anymore and I can login and type some commands, but when I try to go back to the graphical screen with Ctrl-Alt-F7, I get a black screen and the computer hangs, as it did when I got the ugly colors.

I didn't look for the "defoptions" part mentioned in your post, since I don't think changing something that has been commented out would make any difference.

Well, if it didn't work for you then it makes no difference, but the commented out defoptions is used when you get kernel updates. The options from defoptions are added to the new kernels entry line, so if vga=792 would have fixed the problem adding it to defoptions would have made sure you don't have to add it yourself after updates.

Are you using fglrx drivers? I wouldn't have thought that there's too big difference between normal X1600 and Mobility X1600..

---

