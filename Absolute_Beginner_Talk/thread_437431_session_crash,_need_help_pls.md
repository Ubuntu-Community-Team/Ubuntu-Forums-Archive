---
title: "session crash, need help pls"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by sgg on 2007-05-08
Upon login I get the following:

Your session only lasted less than 10 seconds, If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. etc....

/.xsession-errors file

/etc/gdm/PreSession/Default: Registerin your session with wtmp  and utemp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "vfx"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied


I'm a noob here so it could be anything. I may have screwed up some permissions.

I checked the diskspace and there is plenty.

---

