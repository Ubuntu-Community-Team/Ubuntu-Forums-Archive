---
title: "Scanner"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Karolis5000 on 2007-08-14
I have a scanner (CanoScan 3000ex) but it doesn't work. I used XSane by the way. Please help me. I really need to make it work...:(

---

### Post by Arwen on 2007-08-14
The weird thing is that in many forums I've read that there are no drivers for this scanner but I hope I'm wrong and all you need is a little more googling..When you type "lsusb" in terminal can you see your scanner?

---

### Post by linuxwizard on 2007-08-14
That scanner is unsupported will not work
[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

---

### Post by philinux on 2007-08-14
You could try install your scanner software using wine?

worth a shot.

---

### Post by Karolis5000 on 2007-08-15
> **Arwen said:**
> The weird thing is that in many forums I've read that there are no drivers for this scanner but I hope I'm wrong and all you need is a little more googling..When you type "lsusb" in terminal can you see your scanner?
Yes: 
 lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04a9:2215 Canon, Inc. CanoScan 3000/3000F/3000ex
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by Bachstelze on 2007-08-15
This doesn't work in SANE, and most likely never will. Use VMWare for teh win.

---

### Post by Karolis5000 on 2007-08-15
Installed software with wine.... Must be a bug... When I  open it , after few seconds it closes...
I also installed VMware Player but have no idea how to use it.

---

### Post by Arwen on 2007-08-15
Check out the second link:[here]("http://www.google.gr/search?hl=el&q=VMWare+player+manual&btnG=%CE%91%CE%BD%CE%B1%CE%B6%CE%AE%CF%84%CE%B7%CF%83%CE%B7+Google&meta=")
you'll probably need your windows XP CD.

---

### Post by Karolis5000 on 2007-08-15
Um..... Are there any other ways to make my scanner work without using VMware? Its too hard for me...

---

