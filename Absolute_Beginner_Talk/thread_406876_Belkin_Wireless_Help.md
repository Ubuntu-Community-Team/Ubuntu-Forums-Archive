---
title: "Belkin Wireless Help"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-04-11
I just switched to Ubuntu Linux this morning and I havent installed my Belkin Wirless thang yet(im not sure wat there called but it does the same thang as a wirless card but hooks up to the USB port and has a flash drive shape and look to it) and I know alot of people have trouble with Belkin on Linux so some1 please give me step by step instructions.
Ill be very thankful for any help.

---

### Post by Bachstelze on 2007-04-11
Please plug you USB adapter in, open a terminal, type

```
lsusb
```

and paste what you get.

---

### Post by microsoft92sucks on 2007-04-11
paste it were nothing poped up when i plug it in. But the green light on it turned on

---

### Post by Bachstelze on 2007-04-11
[Where's the terminal ?](http://psychocats.net/ubuntu/terminal)

Some image links seem to be broken, tell it to aysiu if yo see him around :)

---

### Post by microsoft92sucks on 2007-04-11
no i got the terminal to comeup by going to it. So paste wat the terminal says on the terminal or should something hav poped up:confused: im srry but this is my first day on linux

---

### Post by Bachstelze on 2007-04-11
Just type *lsusb* and press Enter, some text will appear. Please copy/paste it here.

---

### Post by microsoft92sucks on 2007-04-11
It says
"Bus 001 Device 002: ID 050d:705c Belkin components
Bus 001 Device 001: ID 0000:0000"
thank u soo much for helpinig

---

### Post by microsoft92sucks on 2007-04-11
and wats this ndiswrapper i read about

---

### Post by Bachstelze on 2007-04-11
Youll need to use ndiswrapper. Instructions about it are [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). According to the ndiswrapper Wiki, the driver you need to install is blkwgu.inf, which should be on the CD shipped xith your adapter.

---

### Post by microsoft92sucks on 2007-04-11
so i should put in the installation cd? I thought i shouldent do that since it was made for windows

---

### Post by Bachstelze on 2007-04-11
Precisely. Ndiswrapper is a tool that makes Windows drivers for wireless cards Linux-compatible. And since some makers don't bother t make specific Linux drivers this is quite often the only way to go.

---

### Post by cooldudeny on 2007-08-02
ok so if i will put the cd in it then what ?

---

### Post by anewguy on 2007-08-02
Look on that CD for the file he mentioned (blkwgu.inf).  Once you find it, right click on it and say copy, then go to your desktop and say paste.  Now you have a copy of the driver file on your desktop.  Follow the how-to, pointing ndiswrapper at the ~/Desktop/blkwgu.inf  .  If you have additional questions, post back,  Please let us know how this goes for you.:)

---

### Post by cooldudeny on 2007-08-03
> **anewguy said:**
> Look on that CD for the file he mentioned (blkwgu.inf).  Once you find it, right click on it and say copy, then go to your desktop and say paste.  Now you have a copy of the driver file on your desktop.  Follow the how-to, pointing ndiswrapper at the ~/Desktop/blkwgu.inf  .  If you have additional questions, post back,  Please let us know how this goes for you.:)

does any of these steps require me to be on the internet ?

coz my pc i far and i can connect it with the ethernet cord 

please advice

---

