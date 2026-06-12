---
title: "Serial Mouse Not Recognized"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by steings on 2005-11-23
I only have 1 USB port so I'm using a Serial Mouse on my Laptop.  Ubuntu won't recognize my mouse.  Any Ideas on how to fix this?  Thank You in Advance.

steings

---

### Post by endy on 2005-11-23
I've not done this myself but I found this page in the Ubuntu Wiki:

[https://wiki.ubuntu.com/SerialMouseHowto?highlight=%28mouse%29%7C%28serial%29](https://wiki.ubuntu.com/SerialMouseHowto?highlight=%28mouse%29%7C%28serial%29)

Good luck :)

---

### Post by d1337 on 2005-11-23
That should likely work well.

Another alternative, USB hubs are getting cheap as dirt and are pretty handy for other peripherals.  I picked up a Targus USB number keypad on sale for $15USD and it has two usb ports on it...so it's actually like gaining a port as well.

Of course, the wiki is free...and again should likely work well.

d1337

---

### Post by steings on 2005-11-27
I made the adjustments listed below and the worked great.  I had to do it twice until I got the right ttyS* number.  Thank you

From JeffFortin <https://wiki.ubuntu.com/JeffFortin> Tue Apr 26 00:09:46 +0100 2005 From: Jeff Fortin Date: Tue, 26 Apr 2005 00:09:46 +0100 Subject: quick method Message-ID: <20050426000946+0100@  https://www.ubuntulinux.org> 
For those who are a little bit more experienced with the command line (I was a bit annoyed to have to run through the whole setup and mess all my hand-written config), you can just change this manually into the /etc/X11/xorg.conf file (with nano, vi, or whatever you please), by simply changing Option Device "whateverwastherebefore" to Option Device "/dev/ttyS0" 
Under your mouse section. Be sure to modify the "Protocol" option as well (setting it to "Microsoft" should work). Please see bug number 2346 for more details. 
CategoryDocumentation <https://wiki.ubuntu.com/CategoryDocumentation> CategoryCleanup <https://wiki.ubuntu.com/CategoryCleanup> 
last edited 2005-10-23 15:54:03 by Guidoman

---

