---
title: "[SOLVED] Using usb snoop"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-11-24
After checking the net and looking at the article for building usb snoop support into the kernel, I checked (via modinfo usbcore) the options available in Gutsy and it says usb_snoop is there.  Looking at the file itself, it contains a "N", so I guess instead of using 0 or 1 they have incorporated it using "N" and "Y".  I tried echoing a "Y" to the file using sudo, but it says I don't have permissions.  LS'ing the file would seem to indicate I should be able to do it with sudo.

So, while I know this is a little beyond "absolute beginner talk", using usb snoop as built into the kernel is new to me.  Can someone tell me how to "turn it on", "turn it off", and what I need to look at to see the logging?

Thanks in advance!:)

---

### Post by anewguy on 2007-11-24
Okay, got this figured out, if anyone is interested:

(1) MUST be superuser, can't just use "sudo"

(2) echo Y > /sys/module/usbcore/parameter/usb_snoop

(3) modprobe usbcore

(4) to turn off, repeat (2) replacing Y with N, then repeat step (3)

logfile is in /var/lost/syslog

---

### Post by tdwebste on 2008-06-16
quick and useful, but 

ha ha /var/lost/syslog, something to make sure I read

---

