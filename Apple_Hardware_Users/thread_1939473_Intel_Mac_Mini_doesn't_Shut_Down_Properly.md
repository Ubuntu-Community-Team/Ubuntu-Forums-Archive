---
title: "Intel Mac Mini doesn't Shut Down Properly"
date: 2012-03-11
forum: Apple Hardware Users
---

### Post by Hawkins123 on 2012-03-11
I recently installed Ubuntu 11.10 on my Intel Mac Mini, dual-booted with OSX Snow Leopard. I've been having a problem: the computer doesn't shut down all the way. I get the black screen with text describing the shutdown process, and eventually it says "halting now. system halted", but the computer doesn't turn off. It is the same for GUI shutdown or *sudo shutdown now*. Rebooting is the same, except it displays "rebooting now" instead of "halting now". Any help would be greatly appreciated.

---

### Post by DigiAngel on 2012-03-11
Same here....a 2 GHz machine and 1.83 GHz machine...Live CD does a proper shutdown, Server 11.10 doesn't.

---

### Post by Hawkins123 on 2012-03-11
There's probably some parameter that needs to be modified, but I'm not sure what. To get Ubuntu to boot properly, I replaced "quiet splash" with "acpi=off" in the grub boot parameters. This may be something similar.

---

### Post by Hawkins123 on 2012-03-14
Just installed Oneiric on my HP Compaq and it works fine, so it can't be a problem with my copy.

---

### Post by whiskers751 on 2012-03-15
It doesn't need to physically turn off. It's safe to turn off if you got the halted message!

---

### Post by Hawkins123 on 2012-03-17
Thanks, that's a relief. It would be easier, though, if the machine turned off by itself. Any ideas as to how I should go about fixing it?

---

### Post by Afinity on 2012-03-19
I too have had this problem with 11.10 previously, though a fresh install has fixed it. 
This may or may not help things, but have you tried using the "-h" flag in your shutdown command?
> sudo shutdown -h now

---

### Post by Hawkins123 on 2012-03-19
Yes, I tried that, but the results are the same. Ubuntu itself shuts down fine, but the computer doesn't, so I'm guessing it's some kind of driver problem. I had problems with airport, too, so it would make sense.

---

