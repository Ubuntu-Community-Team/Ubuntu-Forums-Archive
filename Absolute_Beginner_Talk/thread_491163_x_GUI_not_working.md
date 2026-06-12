---
title: "x GUI not working"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Prorally on 2007-07-03
When i run startx the system starts then then screen goes blank and the system stops sendin a video signal. i am runing V5.04 on a 200MMX 96mb of ram

---

### Post by Howler9443 on 2007-07-03
You may be able to determine what is happening by checking the /var/log/X11.0.log file.

There is usually a wealth of information there.

Also, did you try to install nVidia or ATi drivers? If so you should be able to recover the GUI by booting into recovery mode, logging in, and changing the driver back to the original 2D driver in the /etc/X11/xorg.conf file.

The default driver for nvidia is "nv" (you may have "nvidia")  and the default for ATi is "ati" (you may have fglrx)

Hope this helps.

---

