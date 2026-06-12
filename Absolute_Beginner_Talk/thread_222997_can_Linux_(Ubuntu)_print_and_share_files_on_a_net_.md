---
title: "can Linux (Ubuntu) print and share files on a net with only windows machines?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Arijua on 2006-07-25
I have my Cable modem, Belkin router, 1 Desktop, 1 Laptop , 1 Lexmark printer, can I share or print in my lan with my new ubuntu pc? and How!!!

---

### Post by Sef on 2006-07-25
In general Lexmark does not work with GNU/Linux; however, some do, so what type of Lexmark do you have?

---

### Post by brentoboy on 2006-07-25
the short answer: yes

the long answer:
?
does the printer hook to the router via tcp-ip ethernet?

or is it connected up to a windows box via usb or paralelle port?

or do you want it connected to the linux box?

---

### Post by Arijua on 2006-07-25
Well It is a old Z760 but It does not matter to me I can buy other printer, just let me know were to find a list of printer that work with linux, but I want to connect my new ubuntu to my net and share and print, get connected to internet and so, what do I nedd for that, money is no problem

---

### Post by Arijua on 2006-07-25
Yes it is connected via usb to a windows machine

---

### Post by Sef on 2006-07-25
Most HP and Epson work well with GNU/Linux, but they aren't the only ones.  Best site to check for what printers work well with GNU/Linux is [Linuxprinting.]("http://Linuxprinting.org")

If you are going to be doing a lot of printing then either one would be fine.  If you are an occassional printer, then HP is better.

---

### Post by brentoboy on 2006-07-25
make sure that it is shared from the windows computer.

then open nautilus
and type ctrl+l (which lets you edit the location as text instead of buttons)

then, type this up there:

smb://pcname

where pcname is the windows computer that has the printer shared.

that will show you all the stuff that is shared on that box.

if that doesnt work, we need to figure that out before we talk printers.

---

