---
title: "Doh! Just rconfigured Xserver"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by iUSER-Mike on 2007-07-09
Hello, and am greeted by root@username-desktop:~#

Soooo, er , how do I get to the desktop?

Cheers Mike
:lolflag:

---

### Post by iUSER-Mike on 2007-07-09
Okay so I type reboot, the system reboots, look what happened!
[[IMG]http://img451.imageshack.us/img451/5097/linesorbarcodefe8.th.jpg[/IMG]](http://img451.imageshack.us/my.php?image=linesorbarcodefe8.jpg)

Is that an Ubuntu bar code?

:lolflag:

Cheers Mike

---

### Post by overdrank on 2007-07-09
> **iUSER-Mike said:**
> Okay so I type reboot, the system reboots, look what happened!
[[IMG]http://img451.imageshack.us/img451/5097/linesorbarcodefe8.th.jpg[/IMG]](http://img451.imageshack.us/my.php?image=linesorbarcodefe8.jpg)

Is that an Ubuntu bar code?

:lolflag:

Cheers Mike

Hi what type ati card did you install?
You can see which driver is being used in your xorg by using this command
```
gksudo gedit /etc/X11/xorg.conf
```
But as you know any changes you make may crash your xorg so make sure you back up before any changes. Good luck

---

### Post by iUSER-Mike on 2007-07-09
Identifier	"Generic Video CardATI"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	16384

overdrank, Hi, is the above correct?

Cheers Mike:)

---

### Post by iUSER-Mike on 2007-07-09
Wow, just disappeared??????????:confused:

Must be cobwebs in this old Intel Outside pile of museum piece.:guitar:

Cheers anyways

Mike

---

