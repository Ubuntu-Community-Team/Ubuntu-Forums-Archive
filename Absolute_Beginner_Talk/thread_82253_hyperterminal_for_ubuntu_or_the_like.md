---
title: "hyperterminal for ubuntu or the like"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by rexjohnp on 2005-10-26
what, where and how can i install it, is it already present in ubuntu?

---

### Post by Jussi Kukkonen on 2005-10-26
The Hyperterminal I know is a modem diagnostic program made by Microsoft. That is definitely not included in Ubuntu. I doubt it will ever be.

If that's the same hyperterminal you were lookin for, maybe *gtkterm* or *minicom* are usable?

---

### Post by valnar on 2005-11-02
I installed Minicom but can't get it working to my cisco router on my first serial port (COM1 in Windows) to the console port.  I'm not sure which TTY device this is in Ubuntu.  How can I find out?

Robert

---

### Post by ranf on 2005-11-02
[QUOTE=valnar]I installed Minicom but can't get it working to my cisco router on my first serial port (COM1 in Windows) to the console port.  I'm not sure which TTY device this is in Ubuntu.  How can I find out?
[/QUOTE]
COM1: is /dev/ttyS0. The bps rate has to fit or otherwise you get garbage.
It is a good idea to stop and restart minicom after changing settings.

---

### Post by hitent on 2008-07-18
I found a great application called "PUTTY" it is available through Synaptics package manager, or using the sudo apt-get install apt. It is also available for PocketPC and other platforms and the nice thing is that you can use the same client for ssh, telnet, RS232 and Console. Just click on the the type of connection it loads the port/device and works like a charm for /dev/tty/S0. Have not tried it for USB0 on Ubuntu, but have no issues.

---

