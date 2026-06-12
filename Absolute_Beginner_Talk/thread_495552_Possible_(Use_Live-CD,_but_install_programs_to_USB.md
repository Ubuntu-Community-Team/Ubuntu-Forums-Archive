---
title: "Possible? (Use Live-CD, but install programs to USB)"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Genecks on 2007-07-08
I want to be able to use [this]("http://xmacro.sourceforge.net/") inside of Ubuntu. However, it's not included in Ubuntu. Matter of fact, I don't know how to make a Live-CD with it.

Therefore, I figured I might be able to install xmacro onto a jump drive / flash drive.
Would I be able to use a program on Ubuntu if I installed it onto a flash drive and loaded it from the flash drive?

How can I use more programs with Live-CD Ubuntu?
Am I able to install things on a flash drive and load from the flash drive?

---

### Post by chuckyp on 2007-07-08
Absolutely just download build and put it on your usb stick.  You can then launch the app from there.  Linux apps aren't required to be in any specific location to run properly.  If you want to be able to type the name of the app in a terminal to launch it from any folder.  You would have to have the directory that its in, in your path.

Hopefully this made sense.  Try echo $PATH in a terminal to see.  This will show you all folders that are in your users path.

---

