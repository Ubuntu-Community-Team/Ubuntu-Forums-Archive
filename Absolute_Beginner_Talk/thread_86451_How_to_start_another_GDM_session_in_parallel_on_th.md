---
title: "How to start another GDM session in parallel on the :1 ??"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-05
How to start another GDM session in parallel on the :1 ??

(one gdm on the Xscreen :0)
and (another gdm on the X screen :1)

thank you very much !!

Patrick

greetz from belgium

---

### Post by patrick295767 on 2005-11-05
Solved !!
  
So, in the file :
/etc/X11/gdm/gdm.conf
  
please mention that u'll like it in both :0 and :1
That should be indicated as follows :
...
[servers]
# These are the standard servers.  You can add as many you want here
# and they will always be started.  Each line must start with a unique
# number and that will be the display number of that server.  Usually just
# the 0 server is used.
0=Standard
1=Standard
# Note the VTAllocation and FirstVT keys on linux and freebsd.
# Don't add any vt<number> arguments if VTAllocation is on, and set FirstVT to
# be the first vt available that your gettys don't grab (gettys are usually
# dumb and grab even a vt that has already been taken).  Using 7 will work
# pretty much for all linux distributions.  VTAllocation is not currently
# implemented on anything but linux and freebsd.  Feel free to send patches.
# X servers will just not get any extra arguments then.
#
...
  

Regards,

---

