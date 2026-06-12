---
title: "Hal subsystem crashing on suspend, first gen MB 1.8 (hardy)"
date: 2008-02-14
forum: Apple Intel Users
---

### Post by wahr on 2008-02-14
I had this nasty problem where my backlight keys would die on me after resuming (samba is also doing this), and after poking around I found this in the kernel log:

> Feb 14 23:14:31 [computer name redacted] kernel: hald-addon-keyb[27210]: segfault at fffffffd eip b7e427bc esp bfe9cf28 error 4

currently running  2.6.24-rc5macbook kernel (from the prebuilt deb in the recent hardy thread) on my 1.8 ghz core duo first gen machine.

right now I'm working around it by restarting dbus, then gnome-power-manager in a term.

I was advised to write a script to automate this and place it in /etc/acpi/resume.d (along with one to relaunch samba), but i'm not familiar with the format.

---

