---
title: "Device assignment listings"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by eloesch on 2008-01-17
Hello.  I recently started using linux (within 3 months) and I was wondering, is there a command in linux (Specifically Ubuntu Gutsy) to get a listing of devices and their assignments?  For instance maybe USB device port assignments, serial device assignments. etc.  I have worked around computers for about 20 years so I am comfortable using the  command prompt just unfamiliar with the linux OS.  Any help would be greatly appreciated.

---

### Post by PeterJS on 2008-01-17
There's a couple of ways to get information about what's where
lspci, lists everything on the pci bus, it's address and description
lsusb, is the same for the usb bus
lsmod, lists all of the currently loaded drivers
mount, will tell you what file system are currently mounted and where, this is equivalent to cat /etc/mtab

And a whole bunch of stuff more in the /proc/ psuedo filesystem.

Is there something specific you're looking for?

---

### Post by eloesch on 2008-01-24
Thanks for your response PeterJS.  I am completely new to Linux/Ubuntu and still trying to learn my way around.  I was configuring an application called zoneminder and having many problems with my camera configuration.  I finally stumbled onto the correct USB camera port settings to get running, but I thought surely there was an easier way of finding out rather than trial and error.  I have a made up mind to get away from window$ and trying to learn everything that I can.  Any recommended books or materials would be great.  Thanks again.

---

### Post by PeterJS on 2008-01-24
Ask, google,  [Aysiu's guide to Ubuntu](http://www.psychocats.net/ubuntu/), a personal favorite of mine the FHS [short and sweet](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard), [long complete and academic](http://www.pathname.com/fhs/pub/fhs-2.3.html). The Linux Command [guide to shells](http://www.linuxcommand.org/learning_the_shell.php), and the TLDP guide to [Bash](http://tldp.org/LDP/Bash-Beginners-Guide/html/), the tldp guide is more complete but has less basic information. The Ubuntu [Security Guide](http://ubuntuforums.org/showthread.php?t=510812). And last but not least the [ guide to install **anything** on Ubuntu](http://monkeyblog.org/ubuntu/installing/)

---

