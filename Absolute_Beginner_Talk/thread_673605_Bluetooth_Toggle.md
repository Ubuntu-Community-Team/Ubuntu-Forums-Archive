---
title: "Bluetooth Toggle"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by manvsmachine on 2008-01-20
I decided that I really need to develop some scripting skills, so here's my first completed attempt.  This will check if the bluetooth processes are running and enable/disable them accordingly.  Thought I'd put it up for anyone who has both their WiFi and Bluetooth using the same toggle switch.  Just copy and paste this into a text editor and save as btooth_switch.sh (or whatever else you'd want to call it).

[i]#!/bin/bash
if ps -A | grep -c bluetoothd-serv
then
	gksudo /etc/init.d/bluetooth stop
else 
	gksudo /etc/init.d/bluetooth start
fi[/i]

Going into gconf-editor -> apps -> metacity you can set a keyboard shortcut to the script. 
Enjoy.

---

### Post by flitzjoy on 2008-01-23
Worked like a charm. Thank you. ;-)

---

### Post by svguy on 2008-01-23
Thanks! I was just trying to come up with a decent one of these today. Yours works great.

Is there any way to make it so it doesn't prompt you for a password?

---

### Post by manvsmachine on 2008-02-22
not that I know of; by turning off bluetooth you are stopping a system service, which always requires a sudo.  maybe you can somehow include your password in the script, but if so, I don't know how to yet.

---

