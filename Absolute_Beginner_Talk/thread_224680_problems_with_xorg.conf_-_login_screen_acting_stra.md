---
title: "problems with xorg.conf - login screen acting strange"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by jmh754 on 2006-07-28
Alright, I installed Ubuntu 6.06 onto an external USB hard drive successfully, then wanted to get higher screen resolution, so I edited xorg.conf according to one post on these forums or another.  The thing I ran from command line asked all kinds of questions about my peripherals, and drivers and such.  I chose the driver "vga" for my monitor, which I'm pretty sure was wrong, because when I restarted, I got an error saying "driver cannot support 24-bit depth" or something like that.  so I then re-edited xorg.conf according to another post and chose the driver "vesa".  Now when I start Ubuntu, the login screen will appear, but once I login, it jumps to command line, asking for my login again.  Then, after about a minute or so, no matter what I'm doing on command line, it jumps back to the graphical login screen.  Then I login, and back to command line, and so on.  So, any ideas out there?  Is there a way to revert back to default xorg.conf settings?  Any help much appreciated.

Jason

---

### Post by linear on 2006-07-28
To revert, enter this at the command line:

**sudo dpkg-reconfigure xserver-xorg**

---

