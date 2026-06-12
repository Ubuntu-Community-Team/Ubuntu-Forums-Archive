---
title: "Grub"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by majoorke on 2006-08-06
Hello,

I'd like to change my bootloader GRUB , originaly Linux has priority. I mean, Linux is on top of the list. I'd like to change it so that Windows is on top of the list. Therefore I've got to change /boot/grub/menu.lst but I need 'root' permission.

So I go to Konsole and enter "sudo kwrite" or "sudo kate" to use kate or kwrite with 'root' so I can change menu.lst. But when I go to Konsole and I do so,I get a lot of errors like :

```
X Error: BadDevice, invalid or uninitialized input device 166
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-5378' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kdeinit: Shutting down running client.
```

and a lot of : ```
kio (KSycoca): ERROR: No database available!

```
I hope there's an other way to change menu.lst...
Re-installing isn't an option because we've already done that and nothing has changed.

I hope someone here can help me...
Greetz,

Majoorke

---

### Post by anindya_m on 2006-08-06
Hi,
   Seems kate is having problems opening a window as root. As a workaround you can use a text-based editor like nano or vi. So ```
sudo nano /boot/grub/menu.lst
``` should work.

---

### Post by bscbrit on 2006-08-06
Do not use sudo before Kate or Gedit - you will have the problems that you are experiencing here.  To obtain root powers use kdesu (under kubuntu) or gksudo (under gnome).

This link [http://www.ubuntuforums.org/showthread.php?t=203045](http://www.ubuntuforums.org/showthread.php?t=203045) explains it in more detail.

---

