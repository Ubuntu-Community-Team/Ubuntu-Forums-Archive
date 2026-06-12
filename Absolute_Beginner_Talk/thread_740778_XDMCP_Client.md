---
title: "XDMCP Client"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by fepple on 2008-03-31
Hello,

I have setup XDMCP on a Redhat EL5 box and configured it to use the same settings as a local logon (using gdmsetup).  On my Ubutnu desktop I have installed Xnest, this enables the "XDMCP" protocol inside "Terminal Server Client".

However, when I connect to the Redhat machine I get a grey box with the X icon.  [Like this]("http://img442.imageshack.us/img442/4471/screenshotxnestdk4.png").

Any Ideas what is going wrong?

Cheers,
Matt

---

### Post by fepple on 2008-03-31
I've just tried using "Terminal Server Client" using XDMCP to connect to one of our other boxes and it works.  So it must be a problem with how I've setup XDMCP on the redhat box.

Any suggestions still welcome :)

---

### Post by fepple on 2008-03-31
I've fixed it.

On the Redhat box I changed the last line in /etc/inittab

< x:5:respawn:/etc/X11/prefdm -nodaemon
> x:5:respawn:/usr/sbin/gdm

Am not sure exactly what fixed it.  Maybe removing the nodaemon paramater, or some other paramater that prefdm was passing on to GDM.

I'll play with it some more now :)

---

