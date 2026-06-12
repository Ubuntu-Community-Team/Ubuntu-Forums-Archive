---
title: "Robotics,PICprocessors and Basic"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by MarkX on 2008-01-25
Are there any apps like Basic (the programming language) with input/output to printer ports for Ubuntu?
Also, I use PicBasic to program PIC processors, are there any apps available for PIC programming in Ubuntu?

---

### Post by mbrush on 2008-01-25
Hello,

There is a program called Gambas, which is very similar to Visual Basic it's decent, but I've never tried serial/parallel port io in it.

It's actually not very difficult IIRC to control the serialparallel ports in linux, have a look here
[http://www.beyondlogic.org/](http://www.beyondlogic.org/)
I think they have an article on doing in C.

As far as programming, there is 'picprog', which I've not used yet.
You may also consider Microchip MPLAB which as far as I can tell is a Win32 application so it would take a little more work to get it running in Ubuntu.

Good Luck

---

### Post by MarkX on 2008-01-26
Great, Thanks! I'll have a look at those.

---

### Post by Sami_Sdata on 2008-02-24
piklab and gputils.  gputils includes everything you need for PIC assembly.  Piklab is a nice IDE and it will run many programmers.  I have used it with a Pikstart2 to program 16f84, 16f628, and 16f690.

---

### Post by kalaharix on 2008-04-13
[www.arduino.cc](www.arduino.cc) has a hardware solution running from Linux. It has been well described in recent Linux Format magazines.

rgds

---

