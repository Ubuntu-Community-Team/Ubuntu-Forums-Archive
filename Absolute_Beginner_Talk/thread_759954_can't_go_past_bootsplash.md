---
title: "can't go past bootsplash"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-04-19
after the boot splash all i get is a blank screen with a cursor in its top left corner.
I have installed kubuntu desktop in ubuntu and it was working fine till now.Please help.

---

### Post by lswest on 2008-04-19
can you boot into recovery mode (esc at the GRUB countdown, 2nd option) and if so, try removing the "splash" line from the first entry by hitting esc on the GRUB countdown, "e" on the first entry, go down to the 3rd line and hit "e" again, then delete "splash" hit enter and then "b".  Where does it freeze?

---

### Post by sameer.india on 2008-04-19
Well it say's press p for password which i think i have forgotten
By the way i can boot into recovery mode

---

### Post by sameer.india on 2008-04-19
please anyone??????????

---

### Post by sameer.india on 2008-04-19
any answer???

---

### Post by richardjennings on 2008-04-19
when you get to the grub choice shortly after turning on your computer, edit the kernel line and remove quiet and splash. When you boot the modified line, you will get textual updates of whats going on. It should make it possible for you to tell us the last few lines before the boot fails.

---

### Post by sameer.india on 2008-04-19
yes but to do that it asks for a password which i have forgotten

---

### Post by richardjennings on 2008-04-19
well boot into recovery mode, edit /boot/grub/menu.lst & remove the password option. While your at it, remove the quiet and splash options from the kernel line.

---

### Post by sameer.india on 2008-04-19
this gives an error

Warning: unknown mime-type for "/boot/grub/menu.lst" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

---

### Post by sameer.india on 2008-04-19
Well I managed what you said now the screen just goes blank

---

### Post by richardjennings on 2008-04-19
can you post your /boot/grub/menu.lst

---

### Post by sameer.india on 2008-04-19
now?????????????

---

### Post by Absorbed on 2008-04-23
I think I've got the same problem. Gutsy loads the splash screen fine, but when it finishes I get a black screen with a flash of a loading mouse cursor in the centre and a line of television-esque noise at the bottom, and then the monitor acts as if the computer has been turned off.

This doesn't always occur; sometimes the login screen comes up and everything works dandy. You can tell when its worked because the light brown wallpaper appears.

In case anyone is interested, I can get around it by using recovery mode, which boots to a root prompt (I presume that's normal?) and then I type "gdm" to load gnome. To shutdown afterwards I have to alt+ctl+f1 back to the root prompt and type "shutdown -h now". But, obviously, this fix is far from ideal.

---

### Post by Absorbed on 2008-04-23
> **richardjennings said:**
> can you post your /boot/grub/menu.lst

I think this is the appropriate bit:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ab0ecf8b-4c12-4dc5-b44a-b7f0018830a4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ab0ecf8b-4c12-4dc5-b44a-b7f0018830a4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
```

I doubt this is the problem with my computer, because it's worked fine until recently, and I haven't been messing with menu.lst

---

### Post by bumanie on 2008-04-23
Boot into recovery mode and in terminal try > sudo dpkg-reconfigure xserver-xorg 

---

