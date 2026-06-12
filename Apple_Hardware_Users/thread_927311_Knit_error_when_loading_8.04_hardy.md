---
title: "Knit error when loading 8.04 hardy"
date: 2008-09-22
forum: Apple Hardware Users
---

### Post by crapple on 2008-09-22
I have been trying forever to boot hardy heron. I keep getting a blank screen after the splash screen I have changed the xorg file numerous times. Now I am almost sure it is correct. Linux video=ofonly didn't work. Now the computer started giving me this error message. It pops up the terminal (not graphical one just text based) and says
```
Loading, please wait...
kinit: name_to_dev_t(/dev/hda7) = hda7(3,7)
knit: trying to resume image form /dev/hda 7
knit: No resume image, doing normal boot...

Ubuntu 8.041 biggie tty1

biggie login:
```
This happens when I try to boot. It is dual booted with opensuse Linux using hard drive partitioning.

---

### Post by cyberdork33 on 2008-09-22
hardware?

---

### Post by crapple on 2008-09-23
Emac
I don't know the specs of the bat but I can get them later post if you need them. Keyboard works fine not sure about mouse because haven't had graphical interface and that is all that is plugged in
Its a g3

---

### Post by tangibleorange on 2008-09-23
all the kinit message means is that it hasn't found a kinit checks to see if you hibernated and if not, will continue booting normally. The message is perfectly normal!

as for no graphical login, the message you are being presented in a text login. login with ouy usual username and password and then when you have logged in, type:

```
startx
```
and see what happens.

---

### Post by cyberdork33 on 2008-09-23
have a look through the powerpc FAQ:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by crapple on 2008-09-23
Alright I will sumerize what happened when I typed start x
It says pre release of x date september 5th and all sorts of stuff about bug reporting.
X warning process set to prority -1 instead of requested priority 0.
EE Problem parsing config file
EE Error parsing config file
Fatel Server error no screens found
waiting for x to begin accepting connections
conection reset by errno 104 unable to connect to x server
 No such process errno 3 Server error

Not word for word but what I think is important.
Also gives info about operating system

---

### Post by cyberdork33 on 2008-09-23
post your xorg.conf There is an error in it.

---

### Post by crapple on 2008-09-24
Okay it will take me a while because there is no way for me to copy it have to manually type it.

---

### Post by crapple on 2008-09-24
My xorg file appears to have goten screwed up beyond repair. The back up is gone. If I do a fresh install can you post a guide on what changes need to be made to it and what changes need to be made to the yaboot config?
Thank you

---

