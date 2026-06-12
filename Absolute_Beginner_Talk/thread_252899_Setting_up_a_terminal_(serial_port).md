---
title: "Setting up a terminal (serial port)"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-09-07
Hi I am absoulutely new to linux and I just recently installed Unbuntu.

I'm trying to set up terminal for a (DB9) serial port which is connected to a fingerprint board that I want to use.

The manual for setting up my fingerprint board gives me the following instructions :

Start by setting up a terminal (using Minicom, for example) with the following characteristics.:

1) Connection speed :115,200 bps
2) 8 data bits
3) No parity
4) 1 stop bit
5) No hardware control
6) No software control

Okay that is basically what I have to do, however I dont know where to go in the Ubuntu 6.06 LTS to do this. Can I do this from the terminal, if so, how?
Or is there a program (can I click on something in "Appliations", Places",or  "System") in Ubuntu to set up the terminal.


:confused:

---

### Post by mclaren_fan on 2006-09-07
Hi,

You can use minicom, it's in the repositories.
To install: open a terminal and type: sudo apt-get install minicom

---

### Post by cinderella on 2006-09-07
> **mclaren_fan said:**
> Hi,

You can use minicom, it's in the repositories.
To install: open a terminal and type: sudo apt-get install minicom

I tried to install minicom but this is what happened!!!!!

bulletproof@Bulletproof:~$ sudo apt-get install minicom
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package minicom

So what can I do from here?????

---

### Post by Carlos Santiago on 2006-10-29
hi. You could try 'minicom' or 'cu'.
For 'cu' type 'cu -l <serial>
Notice that in Linux, serial ports are identified by:
/dev/ttyS0 (COM1)
/dev/ttyS1 (COM2)
/dev/ttyS2 (COM3)
/dev/ttyS3 (COM4)

So, in a console type 'cu -l /dev/ttyS0' if your device is on COM1

---

