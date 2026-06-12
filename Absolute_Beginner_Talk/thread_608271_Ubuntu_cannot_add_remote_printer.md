---
title: "Ubuntu cannot add remote printer"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by trumants on 2007-11-09
I have 7.10 installed on a Dell Machine with WinXP also installed, lets call it computer 1.  I am trying to connect remotely a printer that is connected via USB to a Vista Premium machine (computer 2).  I have been able to install the printer remotely on the Win XP part of computer 1, but the Ubuntu on computer 1 can't see the printer on computer 2.  The Ubuntu can see computer 2 and has access to the drives and folders.  Any idea what is stopping me on this new Ubuntu install?  I am worse than an newbie when it comes to Ubuntu.:confused:

---

### Post by dwhitney67 on 2007-11-10
Check to see if the printer, which is connected to Computer 2, is being shared.  Then verify that Computer 2 isn't supporting a Firewall that prevents Ubuntu (on Computer 1) from "seeing" the printer.

If none of the above apply, then you have configured the printer incorrectly on your Ubuntu system.

---

### Post by trumants on 2007-11-10
Because Ubuntu is unable to see the printer, I can't configure it.  Maybe I am not using the correct device.  I am trying the "Windows printer via SAMBA" but when it searches for the printer, I go through the workgroup to the printer, to the computer (computer 2) and the search box just blinks and shows the computers on the workgroup.

---

### Post by trumants on 2007-11-11
I found that using the IP address rather than the name worked for me.:)

---

