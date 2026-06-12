---
title: "Virtualbox Question"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Michaelg14 on 2007-10-19
I just installed Virtualbox and have it running with Windows xp.  When I go to settings it tells me:

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

Where or how do I install that service?  I looked in package manager for anything that looked helpful but didn't find anything.

Mike

---

### Post by Daveth on 2007-10-19
is this want you need?

[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

---

### Post by Michaelg14 on 2007-10-19
OK we are making progress, Now I am getting:

Not permitted to open the USB device, check usbfs options.

Where do I find usbfs options.

Mike

---

### Post by Daveth on 2007-10-20
this says:

"If USB is not working on your Linux host, make sure that the current user has permission
to access the USB filesystem (usbfs), which VirtualBox relies on to retrieve valid
information about your host&#8217;s USB devices.
As usbfs is a virtual filesystem, a chmod on /proc/bus/usb has no effect. The
permissions for usbfs can therefore only be changed by editing the /etc/fstab file.
For example, most Linux distributions have a user group called usb or similar, of
which the current user must be a member."

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

goto the user manual, and visit the troubleshooting section, p117 in acrobat reader- lots of cody stuff to play with.

---

### Post by Michaelg14 on 2007-10-20
Thanks for that, I am off to RTFM. :)

Mike

---

