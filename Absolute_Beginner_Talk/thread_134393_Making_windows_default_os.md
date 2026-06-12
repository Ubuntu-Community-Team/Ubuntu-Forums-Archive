---
title: "Making windows default os"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by shickidyshade on 2006-02-21
ok I am a engineer at a college were i have to use windows for all of my classes and i cant get the wireless to work on campus with ubuntu anyway but i was wondering how to make windows my default booting operating system
Shade

---

### Post by RaptorRaider on 2006-02-21
```
sudo gedit /boot/grub/menu.lst
```
Change "default 0" to "saved".
Check whether it says "savedefault" only under "title Windows", if not add it and remove it from all other titles.

I'm sure that with a little bit of effort you should get that "wireless" to work though.

---

### Post by gw90se on 2006-02-21
```
sudo gedit /boot/grub/menu.lst
```

Find the entry shown below and edit the boot number to reflect your windows location in th elist. remember as you count them, the number starts at 0 and goes up.

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

---

### Post by Connollyir on 2006-02-21
[QUOTE=shickidyshade]ok I am a engineer at a college were i have to use windows for all of my classes and i cant get the wireless to work on campus with ubuntu anyway but i was wondering how to make windows my default booting operating system
Shade[/QUOTE]

What problems are you having with your wireless card/network? We might be able to help you out with that. 

-Ian

---

### Post by shickidyshade on 2006-02-21
i am at a university that reguires a secure connection and user login over the wireless any ideas

---

### Post by Connollyir on 2006-02-21
[QUOTE=shickidyshade]i am at a university that reguires a secure connection and user login over the wireless any ideas[/QUOTE]

Well thats likely WPA encryption. Did they give you a key for it? Or is this a staff only deal? If they gave you the key and all your hardware it set up right then its easy to set up.

-Ian

---

### Post by thehybridpyro on 2006-02-21
what is is that I chenge to make windows the default
windows has a chain loader +1 on it

---

### Post by shickidyshade on 2006-02-21
title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


This is what mine displays anyone with ideas

---

### Post by gw90se on 2006-02-21
If I counted right, you should change the default number to 6

---

### Post by shickidyshade on 2006-02-21
what default number im confused

---

### Post by aysiu on 2006-02-21
[QUOTE=shickidyshade]what default number im confused[/QUOTE] You posted only the entries--not the entire menu.lst file. At the top of the file, there should be a line that says: ```
default 0
``` Change that line to say ```
default 6
```

---

### Post by shickidyshade on 2006-02-21
thanks that worked

---

