---
title: "Ubuntu just won't boot anymore"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by TheFluff on 2006-12-01
Ubuntu just hangs at the bootscreen

there's something saying now:

BusyBox(V1.1.3 (Debian 1:1.1.3-2ubuntu3)Built-in-shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs)


it worked just fine, but in some games (nexiuz and another game where the 3d cart gets used (ATI Radeon 9700 Pro) the pc just froze... 

and now it wont boot anymore :s

---

### Post by mushroom on 2006-12-01
have you installed a new kernel recently?

---

### Post by TheFluff on 2006-12-01
i did the automatic updates yes?

---

### Post by mushroom on 2006-12-01
Are you sure that was it? Because, as far as I know, BusyBox is used for embedded systems and shouldn't even be present.

---

### Post by TheFluff on 2006-12-01
hm don't know... :/ 
well, how to get rid of it then?

or at least, how to get ubuntu loading (well, the GUI, i can type in help, and then I get a list of available commands

if i type ls to show the contents of the active folder it shows up correct... so...

---

### Post by mushroom on 2006-12-01
hit escape while Grub's loading, and tell me what your options are.

---

### Post by TheFluff on 2006-12-01
ubuntu, kernel 2.6.17.10-generic
ubuntu, kernel 2.6.17.10-generic (recovery mode)
ubuntu, memtest86+

---

### Post by mushroom on 2006-12-01
Try recovery mode and see if you get a different message. If not, then I have no idea what happened.

---

### Post by Peepsalot on 2006-12-01
> **mushroom said:**
> Are you sure that was it? Because, as far as I know, BusyBox is used for embedded systems and shouldn't even be present.
I have busybox on my edgy install.  I wouldn't bother with trying to get rid of it.  It shows up for me when I do a warm reboot.  For some reason Linux(every form I have tried, not just Ubuntu) refuses to recognize my SATA hard drive when I do a restart.  However, if I turn off the computer for a couple seconds and then power it back on, it will boot up.

---

### Post by TheFluff on 2006-12-01
booting in recoverymode
it hangs at 
... whole lot of numbers] drivers/usb/input/hid-core.c : v2.6 USB HID core driver

the only thing hooked on usb atm is my mouse... 

try without mouse?

oh it got to the point where the normal boot got

done
ALERT! /dev/hdb1 does not exist. Dropping To A Shell!
and then what I got at the first post

---

### Post by TheFluff on 2006-12-01
oh damn


it's fixed

I had changed the IDE cable before I rebooted, because my pc's acting weird lately (beepbibip sometimes, not booting, other times, just normal) and I wanted to know what was wrong... 

So I guess ubuntu is not so happy when you're attaching a cable another way...

Now the only problem is... the hard drive's on slave ](*,) to work... would this cause a slowdown? Nothing's on the master

---

### Post by mushroom on 2006-12-01
My installation runs fine on slave.

---

