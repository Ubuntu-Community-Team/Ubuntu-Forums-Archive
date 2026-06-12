---
title: "nvclock trouble"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by chimera on 2006-02-17
I installed nvclock yesterday and managed to overclock my 6600GT 3d clocks to 550mhz (core clock speed), 1100mhz (memory clock speed) using the coolbits3d backend. After I rebooted my computer, the clock speeds were set back to default (500, 900), and I can't set them back. This happens:

```

chimera@HOMEPC:~$ nvclock -b coolbits3d -n 550 -m 1100
Requested memory clock:         1100.000 MHz
Requested core clock:           550.000 MHz

Adjusted Coolbits 3D clocks on a nVidia Geforce 6600GT
Memory clock:   900.000 MHz
GPU clock:      500.000 MHz

chimera@HOMEPC:~$

```

Does anyone know what could be the cause of this? I tried purging and reinstalling nvclock with apt-get, which didn't yield any results.

---

### Post by Denta on 2006-02-17
Nvclock set options are designed to apply only in the current session, after reboot the settings are lost. What about issuing the same command with sudo?

---

### Post by chimera on 2006-02-17
```

chimera@HOMEPC:~$ sudo nvclock -b coolbits3d -n 500 -m 1100
Password:
Requested memory clock:         1100.000 MHz
Requested core clock:           500.000 MHz

Adjusted Coolbits 3D clocks on a nVidia Geforce 6600GT
Memory clock:   900.000 MHz
GPU clock:      500.000 MHz

chimera@HOMEPC:~$

```

And I didn't have to do it with sudo the first time (before I re-booted), I don't see why I should do it now?

---

### Post by chimera on 2006-02-17
anyone?

---

### Post by Brunellus on 2006-02-17
try asking in the hardware support forum;  I think this is somewhat outside the scope of the Absolute Beginners area.

---

### Post by chimera on 2006-02-17
point taken

---

### Post by jjross on 2006-04-02
I found this article, see if it helps
[http://linuxnetmag.berlios.de/en/issue7/m7nvclock1.html](http://linuxnetmag.berlios.de/en/issue7/m7nvclock1.html)

---

