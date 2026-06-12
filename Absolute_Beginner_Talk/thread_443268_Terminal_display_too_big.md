---
title: "Terminal display too big"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by crazyclown on 2007-05-14
When I run a terminal by pressing CTRL+ALT+F1 the screen resolution is huge.  It seems the resolution is at 800x600 and the font is 40.  I can open Konsole and the resolution is normal.

---

### Post by Cypher on 2007-05-14
CTRL+ALT+F1 is putting you into the standard text console. This is the non-graphical portion of Linux and is fixed font. You just open up Konsole for a terminal. You'd only drop into the text-console if your X-Windows is somehow mis-behaving..

---

### Post by irrer on 2007-05-14
> **crazyclown said:**
> When I run a terminal by pressing CTRL+ALT+F1 the screen resolution is huge.  It seems the resolution is at 800x600 and the font is 40.  I can open Konsole and the resolution is normal.

In your /boot/grub/menu.list there are the listed kernels like this (open with sudo):

title           Debian GNU/Linux, kernel 2.6.20-15-lowlatency
root            (hd0,5)
kernel          /boot/linux-2.6-bla root=UUID=something ro **vga=792**
initrd          /boot/initrd.img-2.6.20-15-lowlatency
boot

I assume your graphics adapter can handle 1024x768. Just add the  bold **vga=792** at the end of the line. After a reboot or ctrl+alt+backspace you should be able to see bootmessages (if no splashscreen is configured) AND your terminal(s) (ctrl+alt+f1) in 1024x768.

Hope this helps and works

Bye

---

### Post by Dr Small on 2007-05-14
Hey, I pressed Ctrl+Alt+F1, but how do I get out of it, besides hitting Control + Alt + Delete ?
Exit doesn't seem to do anything but log me out of the shell. Any other way to get out besides rebooting?

Dr Small

---

### Post by irrer on 2007-05-14
> **Dr Small said:**
> Hey, I pressed Ctrl+Alt+F1, but how do I get out of it, besides hitting Control + Alt + Delete ?
Exit doesn't seem to do anything but log me out of the shell. Any other way to get out besides rebooting?

Dr Small

Nooo reboot required :) 
Just hit ctrl+alt+f7 and you're back.

(ctrl+alt+f1...f6 are your terminals, and ctrl+alt+f7 brings you back to your xserver)

---

### Post by Dr Small on 2007-05-14
> **irrer said:**
> Nooo reboot required :) 
Just hit ctrl+alt+f7 and you're back.

(ctrl+alt+f1...f6 are your terminals, and ctrl+alt+f7 brings you back to your xserver)
Thanks mac. It worked perfectly ;)

Dr Small

---

