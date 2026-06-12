---
title: "scanner problems"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-02-02
i have a scanner that i don't know how to make work with ubuntu.  i don't know what you need to know to help me on this one.  so i'll give some basics.

it is a epson stylus cx4600 printer/scanner/coppier

i turn it on and try to run Xsane.  i get an error message that says there is no device.

umm...anything else you need to know, just ask.

thanks a bunch.


oh, i have used the printer succesfully if that matters.

---

### Post by totfit on 2006-02-02
I too am having scanner problems. I even bought a scanner I thought would work out of the box from the information I found (Epson Perfection 3490). What I have found out is that "supported" does not mean plug and play. I am still working on this issue and I will get it to work when I have the time. This is where you can access the information for supported scanners and information on how to make them work: [http://www.sane-project.org/](http://www.sane-project.org/). Everything else right now is fully functional with my PC and I love Ubuntu. Check out the information on the website and see if it will be helpful.

---

### Post by dotdot on 2006-02-02
ok first off - is the scanner - plugging to a usb port ? if so - plug it in 
then type in 

lsusb ?

ouput - post it up !



..if not - then (I only know about usb.. since my scanner is usb)....

---

### Post by raublekick on 2006-02-02
i was getting that same error even though my printer was working at one point. this may sound dumb, but it's a problem i've had with my printer in both Windows and Ubuntu:

MAKE SURE THE PRINTER IS TURNED ON BEFORE YOU POWER ON THE COMPUTER! For some reason if you turn it on afterwards, or turn it off/on once the computer is running, it won't be detected. hopefully though your problem is not this simple, because it's annoying and i haven't figured out a way to fix it.

---

### Post by insub2 on 2006-02-02
[QUOTE=dotdot]ok first off - is the scanner - plugging to a usb port ? if so - plug it in 
then type in 

lsusb ?

ouput - post it up !
[/QUOTE]


```
insub2@awesome:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 04b8:080d Seiko Epson Corp.
Bus 001 Device 001: ID 0000:0000

```

---

### Post by woopud on 2006-04-15
Upgrade to Ubuntu Dapper and your Epson CX4600 scanner will work right away no setup required!

Bert

---

