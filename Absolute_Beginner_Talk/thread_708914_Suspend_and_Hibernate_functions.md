---
title: "Suspend and Hibernate functions"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by notesetter on 2008-02-26
Hello,

I'm just starting with Ubuntu Studio 7.10, and so far I'm enjoying learning the system. I'm a windows user and am used to the convenience of hibernating when I know I'll be away from my computer for extended periods.

Whenever I try to use the suspend or hibernate feature from the "Logout" area, the screen goes black and a white cursor appears in the upper left of the screen. Nothing else happens. If I push the power button, there is no response. I end up unplugging the power and popping out the battery in order to be able to reboot and then shutdown.

Running:
Ubuntu Studio 7.10

On:
Compaq Presario US2170US Laptop
Intel Celeron 2.0 GHz, 80 GB HD, 256 MB RAM

Thanks,

Dave

---

### Post by glennric on 2008-02-26
What kind of video card do you have?

---

### Post by spiderbatdad on 2008-02-26
I wouldn't put this stuff on my computer, lol, but it claims to enable hibernate/suspend for laptops...[http://www.ubuntugeek.com/howto-tweak-ubuntu.html](http://www.ubuntugeek.com/howto-tweak-ubuntu.html)

---

### Post by notesetter on 2008-02-26
That will take a bit of research. Everything in the machine is original except the HD. Will Linux tell me if I ask it?

---

### Post by glennric on 2008-02-26
Do you know the brand of the card?  Is it nvidia, ati, intel, etc?

---

### Post by glennric on 2008-02-26
Look in the file /etc/X11/xorg.conf and look for a line that says
```
Section "Device"
```
below that there should be information about your video card.

---

### Post by spiderbatdad on 2008-02-26
There are quite a few bug reports on compaqs and suspend issues...this on offers one possible solution: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/20218](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/20218)
Also you need RAM.

grep suspend /var/log/messages

Look for messages which say: "This driver does not support suspend at this time" - You then have to disable those drivers.

I have an ohci1394 driver which does not support suspend and is probably causing the laptop to not come back up. To disable the module just add ohci1394 (firewire) to /etc/modprobe.d/blacklist

---

### Post by notesetter on 2008-02-28
> **glennric said:**
> Look in the file /etc/X11/xorg.conf and look for a line that says
```
Section "Device"
```
below that there should be information about your video card.

Here is the video card information from the file you indicated.

Section "Device"
	Identifier	"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Driver		"ati"
	BusID		"PCI:1:5:0"


Obviously, I'm in no big hurry, so whenever you have the chance...

Thanks a bunch.

Dave

---

