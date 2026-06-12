---
title: "sudo gedit /etc/apt/"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-06-24
manu@kubuntu:~$ sudo gedit /etc/apt/sources.list
Password:
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

i get this when running gedit and when running kate my pc freezes

anyone had this before?

---

### Post by ajmorris on 2007-06-24
> **manuleka said:**
> manu@kubuntu:~$ sudo gedit /etc/apt/sources.list
Password:
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

i get this when running gedit and when running kate my pc freezes

anyone had this before?

in feisty, i always had that when starting a GUI app from a shell, never froze my pc with kate though, and don't know how to fix it i'm afraid :(.... have you reported a bug yet?

---

### Post by kevdog on 2007-06-24
Im not sure why your PC froze, but those error messages are coming from your /etc/X11/xorg.conf file.  All the sections with "wacom" listed need to be commented out (unless by some stroke of God you happen to be running a tablet PC -- are those things even around anymore??).  If you post your file, I'll make the changes and then repost so you can cut and paste.

---

### Post by swisscow on 2007-06-24
Regarding the Wacom stuff, make sure you comment out the corresponding entries in the server section of the xorg as well.

Alternatively let KevDog do it - what a nice guy!

---

