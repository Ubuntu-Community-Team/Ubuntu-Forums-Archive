---
title: "running programs as sudo"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by worstofboston on 2006-07-25
Hi,

I am new to this... I am learning a lot, though.

I have found that there is the sudo terminal program that lets me run whatever I want to as su.

But what if I want to run a GUI as su? I know I can type, for instance, sudo gftp in the terminal - but that wont let me use the graphical interface and if I want to chmod a ton of files I need (or would be seriously helped by) graphical gftp with su permissions.

That is just an example. Is there a command I can type to launch the graphical program in su mode?

Thank you.

JD

Oh yeah... since I have your attention, why am I getting these errors when I launch the SU terminal?
[B][I]
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...


[/I][/B]

---

### Post by reacocard on 2006-07-25
gksudo is the graphical equivalent of sudo. (kdesu for kde)

---

### Post by jmilane on 2006-07-25
I get this error:

[I] (gksudo:29006): Gtk-WARNING **: cannot open display:
[/I]

---

### Post by Engnome on 2006-07-25
> **worstofboston said:**
> 
But what if I want to run a GUI as su? I know I can type, for instance, sudo gftp in the terminal - but that wont let me use the graphical interface and if I want to chmod a ton of files I need (or would be seriously helped by) graphical gftp with su permissions.


sudo can launch gui programs, (not sure why you wanna run gftp as su tho) I usualy laung stuff with sudo instead of gksudo just bc I'm to lazy to type gksudo.

> I get this error:

(gksudo:29006): Gtk-WARNING **: cannot open display:

Running kde?

---

### Post by aysiu on 2006-07-25
Read this: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

The error is not an error at all, just a bug.

---

