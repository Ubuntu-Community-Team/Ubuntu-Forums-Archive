---
title: "Basic Persistent USB capable distro"
date: 2011-08-31
forum: Any Other OS
---

### Post by Catalyst2Death on 2011-08-31
My hard drive died, and so in the meantime (until I get paid to replace the laptop) I need to run some sort of persistent usb distro.

My computer is too old to run natty live off of the usb. 

I need: base system + x11 + emacs + sbcl 

I need to compile stumpwm a lisp based window manager.  I can't find any live usb installs that work.  Also, I don't have access to CD-R media, so I would prefer to be able to install to the usb directly from ubuntu.

I've been trying for three days to figure out an optimal solution, and I can't find anything.  I tried SliTaz which sort of worked, but I couldn't get logged in to run X11.  I also tried rolling my own ubuntu live cd with UCK, but that also didn't work well.

---

### Post by snowpine on 2011-08-31
Puppy, Slitaz, and Tinycore are the most popular for older hardware, from what I've observed.

If you need help with your Slitaz install: [http://forum.slitaz.org](http://forum.slitaz.org)

---

### Post by drawkcab on 2011-09-01
The key is not to depend on a live session but to permanently install the OS onto a second flash drive.

In other words, boot up the live session and, instead of installing it to the hdd, install it to a second usb drive or sdhc card.

---

### Post by Catalyst2Death on 2011-09-01
drawkcab, Is there anything that is different about how I install? I've tried this and with the ubuntu alternative installer, it doesn't work.  I would like to just install a command line system, x, and emacs. But I can't seem to get it to work.

---

### Post by snowpine on 2011-09-01
> **Catalyst2Death said:**
> drawkcab, Is there anything that is different about how I install? I've tried this and with the ubuntu alternative installer, it doesn't work.  I would like to just install a command line system, x, and emacs. But I can't seem to get it to work.

You may find this helpful:

[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

---

### Post by Catalyst2Death on 2011-09-01
I fixed it! I needed to remove:
quiet splash vt.handoff=7 
from the boot options and it booted fine.

---

