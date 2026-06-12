---
title: "X server and graphics drivers"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by jonathanp on 2006-03-17
Finally I've got Ubuntu and Windows XP installed on the same drive (dual boot).
Then I get this message that X - server can't find the right driver for my graphics card.

Does anyone know of an easy way to find out what type of graphics card I have?

---

### Post by codejunkie on 2006-03-17
[QUOTE=jonathanp]Finally I've got Ubuntu and Windows XP installed on the same drive (dual boot).
Then I get this message that X - server can't find the right driver for my graphics card.

Does anyone know of an easy way to find out what type of graphics card I have?[/QUOTE]
when you get into the terminal run ```
lspci
``` and it will list the video card and other devices you have installed.

---

### Post by jonathanp on 2006-03-17
This is what I got:

some numbers followed by: 

VGA compatible controller: VIA Technologies, Inc: Unknown device 3 108(rev 01)

I choose the VIA device controller when installing Ubuntu so I don't know what to do now.
Any help would be great!:-k

---

### Post by jonathanp on 2006-03-17
My Mother board manual says that it has integrated graphics.
does this effect anything?
Should I run the install CD again?
Please help as every time i try something i have to reboot my computer
do start windows when it doesn work!!

---

### Post by codejunkie on 2006-03-17
[QUOTE=jonathanp]My Mother board manual says that it has integrated graphics.
does this effect anything?
Should I run the install CD again?
Please help as every time i try something i have to reboot my computer
do start windows when it doesn work!![/QUOTE]
try using the "vesa" driver on your video card run 
```
sudo nano /etc/X11/xorg.conf
```
find the Section "Device" and edit the Driver line to look like this
```

Driver          "vesa"

```
save the file by pressing ctrl+x and reboot.

---

### Post by jonathanp on 2006-03-17
I tried vesa but I don't actually have a /etc/X11/xorg.conf file
I edited the /etc/X11/XF89Config-4 file
Then I rebooted and x server starts but the screen is very "chopy" and 
is unusable.
Are there any other drivers I can use?

Thanks for your help!
I really like linux but I'm starting to discover its downside (driver incompatibility).

---

### Post by jonathanp on 2006-03-17
Note I'm using Ubuntu version 4.10 (Intel x86) does this use the xorg.config
or XF86Config-4 file?

---

