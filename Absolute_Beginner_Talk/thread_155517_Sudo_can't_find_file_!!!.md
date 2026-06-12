---
title: "Sudo can't find file !!!"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by Ric95 on 2006-04-05
I need to change the default boot menu, and of course I need sudo for roop permission to do that. When I look at the file I need it just looks like its located at 'boot/grub/menu.lst'
I have tried;
sudo nano /boot/grub/menu.lst                   ....'file not found'
sudo nano system files/boot/grub/menu.lst  ....'file not found'
I can open 'sudo nano' and get the text editor with hotkey list at the bottom, but cont-R , boot/grub/menu.lst               .....'file not found'
What is wrong with this location ](*,)

---

### Post by Jason_25 on 2006-04-05
So does
```

nano /boot/grub/menu.lst

```
work?

---

### Post by meborc on 2006-04-05
[QUOTE=Ric95]What is wrong with this location ](*,)[/QUOTE]

are you sure you are doing 

**sudo nano /boot/grub/menu.lst**
and not
**sudo nano boot/grub/menu.lst**

the first one works... the second one works also if you are 'browsed' to /

---

### Post by mlind on 2006-04-05
if command *dpkg -l 'grub'* says that grub is installed

then *sudo nano /boot/grub/menu.lst* should work.
If you have /boot on separated partition, see if it's mounted.

---

### Post by Ric95 on 2006-04-05
Thanks for the replies. :)
I was lacking a '/' one try, and 'sudo' the next... ( Im such a noob..again.:) )
Now I can get that to work, but I still need to figure out how to save the edited file. The save function under 'file' doesn't work, and I didn't see a save hotkey in the list at the bottom.

---

### Post by sn123 on 2006-04-05
[QUOTE=Ric95]Thanks for the replies. :)
I was lacking a '/' one try, and 'sudo' the next... ( Im such a noob..again.:) )
Now I can get that to work, but I still need to figure out how to save the edited file. The save function under 'file' doesn't work, and I didn't see a save hotkey in the list at the bottom.[/QUOTE]
sorry top off my head but doesn't hitting CTRL-X prompt you to save the file before exiting? otherwise use gedit unless you're in console mode.
```

$ sudo gedit /boot/grub/menu.lst

```


S

---

### Post by Ric95 on 2006-04-05
Thanks. I figured out hotkey for 'write-out was what I needed, but for the future gedit will probably suit me better.

---

