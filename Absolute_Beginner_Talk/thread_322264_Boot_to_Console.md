---
title: "Boot to Console"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by gregski on 2006-12-20
Hi,

Ok, here's one for all you old school linux folks out there!  I'm a newbee using Ubuntu 6.10 and I would like to boot to the console.  Xserver is not to load (but is installed).
I've looked at changing the runlevel, via /etc/event.d but can't figure out how to do that.  It also looks like run levels 2 and upwards are all GUI anyway.
The reason for this is to create a mainframe terminal that will connect to an AS400 using the TN5250 program as the client.  This will run in GNOME, but is visually better using a good ole console.  I would therefore like to avoid booting xserver.
I can accomplish this easily in Fedora but would prefer to use Ubuntu.
Any ideas are greatly appreciated!

---

### Post by Sef on 2006-12-20
If I remember correctly, when you get to the login window, click on options and you can chose how you want to boot in.  Just click on default if it asks you to make it the default.

---

### Post by gregski on 2006-12-20
Thanks for the reply.
Yes there is a Failsafe Terminal option.  But I still get a semi-gnome desktop and the terminal session appears in the bottom right corner of the screen (my default screen resolution is 1024x768).  At next bootup, the option must be selected again.
I want to boot straight to a command line with black screen and basic resolution.  A login prompt (not login window) should be seen.

---

