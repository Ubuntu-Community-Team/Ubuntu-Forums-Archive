---
title: "USb to Serial cable not detecting"
date: 2012-05-20
forum: Any Other OS
---

### Post by jovin555 on 2012-05-20
i am using linux mint 12.i installed gtkterm.i want to connect a gsm modem using usb to serial.but when i open the gtk serial i cant send any data.i have given /dev/ttyUSB0 in configuration and set 9600 as baudrate.Still not working.what will be the problem?

---

### Post by Perfect Storm on 2012-05-20
Moved to Other OS/Distro Talk.

---

### Post by miegiel on 2012-05-20
Maybe you need drivers from *contrib* or *non-free* for the gsm modem.

An exaple from my /etc/apt/sources.list (in debian):
```
deb http://mirrors.nl.kernel.org/debian/ wheezy main **[COLOR="Red"]contrib non-free[/COLOR]**
```

---

### Post by jovin555 on 2012-05-21
how can i install those drivers?can u help with the commands in terminal for installing those drivers?

---

### Post by miegiel on 2012-05-21
> **jovin555 said:**
> how can i install those drivers?can u help with the commands in terminal for installing those drivers?

Can you post the terminal output of the following commands (in a code box please, to avoid annoying smilies)
```
uname -a
```
```
lsusb
```
```
cat /etc/apt/sources.list
```
```
sudo lshw -short
```
I've got to say installing drivers in linux always gives me a headache. :) I'm so used to plugging things into my machine that just work without having to install anything, that I feel a little lost when it doesn't.

---

