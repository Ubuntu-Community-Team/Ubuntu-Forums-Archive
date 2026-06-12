---
title: "Anyone have a working Macbook Gutsy xorg.conf?"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by sgithens on 2007-10-23
Hi, after installing Gutsy on my first gen MacBook, everything was great, until I tried to work with an external display and I messed up the config.

I've tried the bulletproof screen, both the utilities on the System Menu, dpkg-reconfigure xorg-server, apt-get install 915resolution,  etc and I just can't get back to 1280x800.

Does anyone have a working xorg.conf file they could share? ( I need to give a presentation tomorrow morning.  :)   )

Also, there used to be a really great xorg.conf available at [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

but all the pre Gutsy documentation seems to have disappeared.  Does anyone know how I can find that previous page?  If only I had that xorg.conf!!  :)

Thanks,
Steve

---

### Post by sgithens on 2007-10-23
I was able to find the revision of the wiki from September that had the xorg.conf info, so hopefully I'll be able to get it from that.

---

### Post by cyberdork33 on 2007-10-23
use the intel driver as opposed to the i810 driver

---

### Post by onyxrev on 2007-12-20
Enclosed is mine, which has been working swimmingly.  It enables two-finger scrolling and right clicking if you use load the appletouch driver in your /etc/modules.

---

