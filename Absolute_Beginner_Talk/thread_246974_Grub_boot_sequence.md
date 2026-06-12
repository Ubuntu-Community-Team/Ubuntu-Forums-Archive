---
title: "Grub boot sequence"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by deadspeak on 2006-08-30
hi chaps
is there any way to edit the grub boot sequence so i can move Win xp into the number one position 

thanks in advance

---

### Post by etc on 2006-08-30
Yup.

open a terminal and type
```
gksudo gedit /boot/grub/menu.lst
```

Go to the bottom of the file and look for a second that looks like
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
it doesn't have to be exact

Cut that whole section, then place it ABOVE the very first section that looks like
```
title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot
```

save the file, and your grub list should now have windows on the top

---

### Post by amo-ej1 on 2006-08-30
sure it is possible, you could edit /boot/grub/menu.lst (which contains all the entries you see in your grub menu). And one of the first lines not starting with # says something like "default 0" this is the index of the default image that gets loaded, so you either have to increase this number to  match the windows entry. Or you move the windows entry up in the list (by moving the definition up). But it's easier to fiddle with the default setting ;-).

And now i've got to ask, are you really sure you want to do that [-(

---

### Post by mcduck on 2006-08-30
> **etc said:**
> Yup.

open a terminal and type
```
gksudo gedit /boot/grub/menu.lst
```

Go to the bottom of the file and look for a second that looks like
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
it doesn't have to be exact

Cut that whole section, then place it ABOVE the very first section that looks like
```
title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot
```

save the file, and your grub list should now have windows on the top
If you do that, you also make sure that you paste the Windows above lines like:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
If you paste it inside the 'automagick area' it will disappear when next kernel update modifies Grub to use new Linux kernel.

It's better to instead just change the default number like amo-ej1 wrote. Or you can change the 'default 0' to 'default saved' to make your computer always boot to last used OS by default.

---

