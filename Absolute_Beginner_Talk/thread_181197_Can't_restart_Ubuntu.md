---
title: "Can't restart Ubuntu"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by markfasano on 2006-05-23
I just installed Ubuntu alongside Windows on my Sony notebook and most everything is working great. One snag, however, is that Ubuntu can't restart. When I go into Log Out>Restart Ubuntu closes down and then hangs. Black screen, nothing. The computer is still on. Eventually I have to force quit and then reboot from scratch. Any ideas?

Mark

---

### Post by tuxcantfly on 2006-05-23
does it reboot if you open up the terminal (applications - accesories - terminal) and typing this:

sudo init 6

---

### Post by markfasano on 2006-05-24
no, it goes to a black and white "Breezy Badger" login page, the cursor blinks for about 15 seconds, then the screen disappears and the computer hangs again. it has to be force quitted.

---

### Post by lucia_engel on 2006-05-24
[quote=markfasano]no, it goes to a black and white "Breezy Badger" login page, the cursor blinks for about 15 seconds, then the screen disappears and the computer hangs again. it has to be force quitted.[/quote] 
I used to have that problem. Try this:

Launch the Terminal,
Type
```
sudo gedit /boot/grub/menu.lst
```

Go to the section that looks similar to this

```

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

```
add reboot=h to the end of kernel line

kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda3 ro quiet splash reboot=h

FYI, the problem is fixed in Dapper for me

---

### Post by markfasano on 2006-05-24
that got it. thanks. BTW, I have 386 on the end of my kernel string, not 686. what's up with that? thanks again.

---

