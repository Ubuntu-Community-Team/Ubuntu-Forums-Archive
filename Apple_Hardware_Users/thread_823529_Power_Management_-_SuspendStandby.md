---
title: "Power Management - Suspend/Standby"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by henryrhenryr on 2008-06-09
Hi

I'm on an Apple iMac G3 233 tray loading.  I have Xubuntu 6.06 which runs nicely!

I'm trying to get it to suspend or standby using the terminal.  Actually I can't even get it to suspend using the GUI.

I have seen quite a few references to ACPI and APM.  I don't seem to have any of the mentioned ACPI files or folders.  APM has a folder but I can't seem to use it.

Is it that Xubuntu shipped without the necessary bits or is it that my old iMac is not capable of suspend or standby?  If it can go into suspend or standby, can someone tell me how to do ths from terminal/command line.

Thanks!

Henry

---

### Post by Kobalt on 2008-06-09
Suspend / Hibernate is very much tied to the hardware support of the distribution you use. Ubuntu 6.06 is quite an "old" distribution now, you should try the next LTS version, being Ubuntu 8.04. It has much improved hardware support, that should be a good start. 
You can upgrade from one LTS version to another [this way]("https://help.ubuntu.com/community/GutsyUpgrades").

---

### Post by jimmy the saint on 2008-07-20
solution here: [http://ubuntuforums.org/showthread.php?p=5424711#post5424711](http://ubuntuforums.org/showthread.php?p=5424711#post5424711)
it is a matter of power manager being helpless without gnome-screensaver.  check out that post for an easy solution!

---

