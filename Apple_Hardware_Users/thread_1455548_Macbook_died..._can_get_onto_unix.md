---
title: "Macbook died... can get onto unix"
date: 2010-04-16
forum: Apple Hardware Users
---

### Post by MacAodh on 2010-04-16
Hi all,
I have a bit of a problem, I managed to get my macbook to freeze on the start up so I can't turn on my computer. This is not the first issue I've had with mac so I wanted to switch to ubuntu (esp with the new one. looks really good...)

Anyway, for some reason loading from a either a CD or usb doesn't seam to be working, Is there a way, from unix, I can force the computer to use the usb key or cd?

Thanks a mill guys

---

### Post by linuxopjemac on 2010-04-16
boot with option key and CD in, that should give you the boot options

---

### Post by MacAodh on 2010-04-16
> **linuxopjemac said:**
> boot with option key and CD in, that should give you the boot options

No joy, just spat out the CD and started the circle thing spinning...

---

### Post by linuxopjemac on 2010-04-16
try resetting pram

boot with option+command+"p"+r" keys pressed, untl you hear a second boing, then try to boot from CD by holding option or "c"


NB
p+r as in pram reset

---

### Post by MacAodh on 2010-04-16
> **linuxopjemac said:**
> try resetting pram

boot with option+command+"p"+r" keys pressed, untl you hear a second boing, then try to boot from CD by holding option or "c"


NB
p+r as in pram reset

Did that and still nothing.

The cd spools up then dies, spools up then dies a few times before being spat out.
Also tried with a usb key both in and out

---

### Post by linuxopjemac on 2010-04-16
go see the doctor....Apple repair ?

---

### Post by MacAodh on 2010-04-16
> **linuxopjemac said:**
> go see the doctor....Apple repair ?

Is that going be the only option??? Surely I can format the hard drive via UNIX and then load ubuntu or something!!!

---

### Post by linuxopjemac on 2010-04-16
You can't even boot anything! How would you plan to do that ?

---

### Post by MacAodh on 2010-04-16
> **linuxopjemac said:**
> You can't even boot anything! How would you plan to do that ?

If I press command +s I can get into the UNIX command line

---

### Post by linuxopjemac on 2010-04-16
interesting, I didn't know this. Can you do something useful there ?

---

### Post by MacAodh on 2010-04-16
> **linuxopjemac said:**
> interesting, I didn't know this. Can you do something useful there ?

Any suggestions would be appreciated... I like gui... command lines scare me

---

### Post by linuxopjemac on 2010-04-16
what happens if your force X to boot ?

command + x

see [http://mac.linux.be/content/ten-different-boot-options-leopard](http://mac.linux.be/content/ten-different-boot-options-leopard)

or safe mode (hold Shift)

---

### Post by MacAodh on 2010-04-16
> **linuxopjemac said:**
> what happens if your force X to boot ?

command + x

see [http://mac.linux.be/content/ten-different-boot-options-leopard](http://mac.linux.be/content/ten-different-boot-options-leopard)

or safe mode (hold Shift)

Hummm... Very interesting list, thanks.

Safe Mode - Comes up with a status indicator. After about a third of the way it disappears and goes back to just that spinning ball of hate.

x - doesn't seam to give any difference.

Verbose mode - Lots and lots of error messages. Most of them too fast but finally come up with repeating 4 lines:
SATA WARNING: Enable Drive PHY PM Failed
disk0s2: I/O error.
disk0s2: I/O error.
disk0s2: I/O error.

---

### Post by linuxopjemac on 2010-04-16
Maybe a broken hard disk or something like that ?

---

### Post by MacAodh on 2010-04-16
> **linuxopjemac said:**
> Maybe a broken hard disk or something like that ?

I thought that but it doesn't really make sense. I was using it and it froze and then restarted it... plus, should I be able to get into unix then???

---

### Post by linuxopjemac on 2010-04-16
I can't help you with this. I would go to see an Apple repair center and ask those people.

---

