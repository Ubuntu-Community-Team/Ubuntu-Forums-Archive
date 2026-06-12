---
title: "Help! xubuntu is locking up on the Live CD install"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by XeroCurve on 2006-10-13
I am looking for an alternate way of installing xubuntu on my laptop. I installed Ubuntu with Gnome on it fine and used it for a while, I even installed the XFCE desktop on the Ubuntu install and that worked fine, but I want to install xubuntu fresh but it locks up on the install. I am using an ISO that I burnt. I know the ISO works because I used to install on another Desktop PC yesterday. Do I need to use the Alternate ISO? Is there a way of doing the xubuntu install from the command line.

Dell Inspiron 2650
Celeron 1.6 ghz
256 RAM

HELP !!!

---

### Post by Kateikyoushi on 2006-10-13
Give the safe video mode a try before you burn that alternate install cd.

---

### Post by XeroCurve on 2006-10-13
Ok I tried the Safe Graphics Mode and I got something a little different this time. I got an "Installer Crashed" window that popped up it said this in it.

---------------------------------------------------

Installer Crashed

Were sorry; the installer crachsed. Please file a new bug report
at [https://launchpad.net/distros/ubuntu/+source/ubiquity/](https://launchpad.net/distros/ubuntu/+source/ubiquity/)
+filebug (do not attach you details to any existing bug) and a
developer will attend to the problem as soon as possible. To
help the developers understand what went wrong, include the following detail in your bug report, and attach the files
/var/log/installer/syslog, /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):

File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 710, in on_next_clickedgtk.main_quit()

RuntimeError: called outside of a main loop

---------------------------------------------------

So I guess I will do that, but in the mean time does anyone have any comments?

---

