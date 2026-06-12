---
title: "shut down problem"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-02-20
After a few works with firefox, texmaker, xdvi when I try to shut down/reboot/logout, Ubuntu hangs.:( 
Can anyone help me?

---

### Post by tbroderick on 2007-02-20
Use top to check and see what's running before you shutdown.

---

### Post by kjacks on 2007-02-20
You could always open a terminal and force it to shutdown.  It's not very graceful, but it's never failed me.

sudo shutdown -h now

---

### Post by hardyn on 2007-02-20
try opening /boot/grub/menu.lst

add vga=780 to the end of the boot string for the kernel that you are currently using.

i have had to do this on all my machines, espicially ones with ATI graphics.

---

### Post by sauravbhaumik on 2007-02-20
> **tbroderick said:**
> Use top to check and see what's running before you shutdown.

Actually what I have managed to have found out is that evince the document viewer eats up the cpu. When I scroll pages down and up in evince, the cpu usage surges up to 60 or 72%.:( 
And when I use texmaker and evince together, it hangs up!:cry: 
Any solution?

---

