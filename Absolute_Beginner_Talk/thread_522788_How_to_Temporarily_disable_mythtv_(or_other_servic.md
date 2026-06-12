---
title: "How to Temporarily disable mythtv (or other service)"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by jc508 on 2007-08-11
Hi,
I need to stop Mythtv backend from trying to work until I sort out problems with the tuner card. 
I can see /etc/init.d/mythtv-backend  but have no idea what calls it in the boot sequence.
Was hoping to just comment out a line for a while

Any help appreciated.

JC

---

### Post by DBStevens on 2007-08-11
Does myth show up in System > Administration > Services if it does you should be able to uncheck it there and it will be shutdown and not start again until you check it again.

If it isn't there you can turn off the execute bit by issuing:

sudo /etc/init.d/mythtv-backend stop
sudo chmod -x  /etc/init.d/mythtv-backend

---

