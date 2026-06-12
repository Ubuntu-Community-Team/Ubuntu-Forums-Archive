---
title: "setting serial baud rate"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by matpark01 on 2005-07-22
Managed to work out that my slow modem connection was because my serial port (ttyS0) was set at 9600. I have worked out I can chnage that using stty but when switch off the serial port reverts to 9600. Is there any way to get it to remember the higher rate from boot up?

---

### Post by aleXL on 2005-08-14
Taken from 'nuther thread:

type this in a terminal (substitute your correct port number for "<XX>":

stty -F /dev/ttyS<XX> speed 115200

Typing this once will tell you what it is now set at (probably 9600), typing 
it a second time will set it to 115200. If that works, then if you want that 
port (modem) set to 115200 at every boot, do this:

sudo gedit /etc/init.d/bootmisc.sh

And add the previous line to the bottom of the file and save. In my case my 
modem is on ttyS14 so this is the line I added:

stty -F /dev/ttyS14 speed 115200

---

