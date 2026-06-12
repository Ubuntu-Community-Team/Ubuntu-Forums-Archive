---
title: "Jaunty, wireless, 24 inch imac"
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by learning on 2009-04-26
Just installed Jaunty on my 24 inch imac (2.8 ).  Everything seems to work so far, had to play with sound, and it is a bit muted, but working.  My problem is with the wireless.  Every time I reboot I have to run the following commands:

sudo rmmod ssb
modprobe wl

sudo depmod -a

to get my wireless working.

I'm still pretty much a noob as most of my computers have worked pretty well with ubuntu out of the box.  How do I fix this?  Do I need to make a script to do this every time on start-up?

Thanks for the help!

---

### Post by cyberdork33 on 2009-04-27
> **learning said:**
> Just installed Jaunty on my 24 inch imac (2.8 ).  Everything seems to work so far, had to play with sound, and it is a bit muted, but working.  My problem is with the wireless.  Every time I reboot I have to run the following commands:

sudo rmmod ssb
modprobe wl

sudo depmod -a

to get my wireless working.

I'm still pretty much a noob as most of my computers have worked pretty well with ubuntu out of the box.  How do I fix this?  Do I need to make a script to do this every time on start-up?

Thanks for the help!
You could try disabling the Broadcom STA driver in System > Administration > Hardware Drivers, reboot, then reenable it again, and reboot.

Or, you can

blacklist ssb in /etc/modprobe.d/blacklist

add 'wl' to your /etc/modules file.

---

