---
title: "System Specs?"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by masooga on 2006-03-14
Is there an easy way to display your system specs in ubuntu?

Thanks

---

### Post by aysiu on 2006-03-14
Yes.

Are you using Gnome or KDE?

---

### Post by masooga on 2006-03-14
Gnome

---

### Post by aysiu on 2006-03-14
Have you tried Alt-F2 ```
gnome-system-monitor
```?

---

### Post by masooga on 2006-03-14
I'm looking for my processor, video card, etc.  that doesn't seem to be in the system monitor?

---

### Post by aysiu on 2006-03-14
Does Alt-F2 ```
hwdb-client
``` do anything?

---

### Post by masooga on 2006-03-14
Nope :-?  sorry

EDIT

Oops, it says:

Cannot display location 'file://hwdb-client'

Details: There is no default action associated with this location.

---

### Post by KansasJoe on 2006-03-14
try this            sudo lshw > hardware.txt

---

### Post by masooga on 2006-03-14
That just lists a few three letter words very quickly and ends on USB.  From their I can't do anything.

---

### Post by KansasJoe on 2006-03-14
now look in your home for that file and it will show all of your specs

---

### Post by KansasJoe on 2006-03-14
or you could do in terminal

cat hardware.txt

---

### Post by bluevoodoo1 on 2006-03-14
Also there's...

lspci
cat /proc/meminfo
cat /proc/cpuinfo

---

### Post by masooga on 2006-03-14
Thanks!  That helped a lot!:D

---

### Post by KansasJoe on 2006-03-14
just happy to actually help someone instead of being helped

---

