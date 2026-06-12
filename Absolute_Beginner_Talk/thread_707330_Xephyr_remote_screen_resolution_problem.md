---
title: "Xephyr remote screen resolution problem"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by 01000111 on 2008-02-25
Greetings all,
Here's my setup:

Machine A:  Xubuntu 7.10, 2 monitors each running 1280x1024
Machine B:  Xubuntu 7.10 AMD64 connected to a HDTV running at 1920x1080, with a default font size of 40.

I've set machine B's Login Window Preferences to enable remote login as "Same As Local", and unchecked "Deny TCP connections to Xserver"


Using Xephyr I can connect from machine A to machine B, logon and see the desktop using the command:

Xephyr :30 -query 192.168.1.5

The problem is that I can't seem to change the resolution so I can see the whole of Machine B's screen in a window on Machine A.

I've tried:

Xephyr :30 -query 192.168.1.5 -dpi 100
Xephyr :30 -query 192.168.1.5 -dpi 200
Xephyr :30 -query 192.168.1.5 -dpi 400
Xephyr :30 -query 192.168.1.5 -screen 640x480
Xephyr :30 -query 192.168.1.5 -screen 800x600
Xephyr :30 -query 192.168.1.5 -screen 800x600 -dpi 200

but they all produce the same result as if there was no -dpi or -screen option set and the screen is too large to see.

Any thoughts?

TIA

01000111

EDIT:
Ok...  for some reason I wasn't thinking clearly...  I've changed the -dpi 15 and the fonts are good, but the size of the screen is still too large.  Little help...?

---

