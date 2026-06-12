---
title: "change printer margins?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-17
i've had many problems with my samsung ml-2010 laser printer running on ubuntu. from what i've heard it works on other distros, just not ubuntu. is there some kind of way to compensate for the marginal errors? one workaround is adjusting page setup before printing every single time, but i was wondering if there was a better way or maybe a permanent adjustment as such. i need help!

---

### Post by mitch.c on 2006-10-17
> **shanepardue said:**
> i've had many problems with my samsung ml-2010 laser printer running on ubuntu. from what i've heard it works on other distros, just not ubuntu. is there some kind of way to compensate for the marginal errors? one workaround is adjusting page setup before printing every single time, but i was wondering if there was a better way or maybe a permanent adjustment as such. i need help!
Have you tried:
```
# replace printername appropriately; sets top margin to 0.5" (36 pts.)
# also use page-left, page-right, page-bottom.
lpoptions -p printername -o page-top=36
```

---

### Post by shanepardue on 2006-10-17
i'm sorry..what file am i entering this into? i'm assuming cupsys, but i'm not near a linux computer.

---

### Post by mitch.c on 2006-10-17
> **shanepardue said:**
> i'm sorry..what file am i entering this into? i'm assuming cupsys, but i'm not near a linux computer.
Enter at a shell prompt
```
user@ubuntu:~$ lpoptions -p printername -o page-top=36
```

---

### Post by shanepardue on 2006-10-17
oh i see..i typed the following commands and rebooted to find nothing had changed.

```
lpoptions -p MFP_USB_Port_0 -o page-bottom=36
```

i wanted to give myself 1/2" on the bottom. i also put 0 for the top.

---

### Post by steve.horsley on 2006-10-17
I'm no expert, but that printer name looks suspect to me. I don't know how you find out what names are acceptable/appropriate though.

---

### Post by shanepardue on 2006-10-17
i got it working. what fixed it was...setting the paper size to letter through [http://localhost:631/](http://localhost:631/) and not just through cups manager. now i'm printing with great margins on all of my computers in the network!

---

### Post by steve.horsley on 2006-10-19
So the printer name was right? Well, you learn something every day.  Well done.

---

