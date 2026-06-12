---
title: "re scan grub?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by cypher_666 on 2007-02-13
hi there.

i recently decided to do away with my windows partition and just have kubuntu on my laptop. however the grub is still showing XP as a boot option, is there any way i can re scan it as it were and make it see that XP is no longer there and make it automatically load into kubuntu instead of asking me?

thanks in advance for the help.

---

### Post by arthurD on 2007-02-13
Open /boot/grub/menu.lst with a text editor (you need to be root), and remove the windows entry. That should do the trick.

---

### Post by cypher_666 on 2007-02-13
cheers, ill give that a shot :)

---

### Post by nsleiman on 2007-02-13
go to the console (or konsole?) and type: sudo nano /boot/grub/menu.lst

look for the lines where title is Windows xxx and delete this entry :)

btw if you are on gnome u must replace nano with gedit.

---

### Post by nsleiman on 2007-02-13
go to the console (or konsole?) and type: sudo nano /boot/grub/menu.lst

look for the lines where title is Windows xxx and delete this entry :)

btw if you are on gnome u must replace nano with gedit.

---

### Post by cypher_666 on 2007-02-13
thanks, worked like a charm :)

---

