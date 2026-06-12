---
title: "9 pin serial port under Ubuntu and downloading blood glucose machine"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Cloudedbrains on 2007-05-27
Is it possible at all to use a 9 pin serial port under Ubuntu ???

Its just my diabetes blood glucose machine uses a 9 pin cable to download ???

This is the meter I use and their software is linked to here too:
[http://www.abbottdiabetescare.co.uk/products/mini.php](http://www.abbottdiabetescare.co.uk/products/mini.php)

Do you think I have any chance of getting this workign under Ubuntu ???

---

### Post by Stephen Howard on 2007-05-27
Probably worthwhile experimenting with it.  You can certainly access the serial ports (9 pins) in linux.  A port is just /dev/tty entry which you can easily configure.

The hardest bit will be figuring out the command codes that you presumably need to upload to the unit to tell it to download its data.  The next hardest bit will be figuring out the data structure that it downloads so that you can then write a program to interpret it.  That said, maybe the company's windows software will run under wine??

---

### Post by Cloudedbrains on 2007-05-27
I tried everything and it wont work so have decided to go dual boot again - as its important I can access the blood sugar meter :(
So am re-installing XP and will then go the Wubi route again :p

I luv Ubuntu but there are things I need XP for it seems :o

---

