---
title: "How do I see my drivers?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-08-26
How do I see a listing of devices and the installed drivers for these devices? (particularly display) How do I change these drives if they arn't the right one?

---

### Post by PaulFr on 2007-08-26
Some suggestions (check the manual pages for more details):

**lshw**, **lsusb**, **lspci** will give you your device information. 

**lsmod** will give you the modules loaded in the kernel.

After a reboot, **dmesg** will give you the boot up messages (which include details of drivers). Otherwise you have to look through **/var/log/messages**.

---

### Post by schorsch on 2007-08-26
A list of devices can be obtained via
```
lshw
```
If you are looking for the display drivers just type:
```
lshw -C display
```
The used driver can be changed via editing the file /etc/X11/xorg.conf. but make a backup of the file first!!
Another way to change the drivers is
```
sudo dpkg-reconfigure xserver-xorg
```
but again: Make a backup of the file /etc/X11/xorg.conf first!!

---

