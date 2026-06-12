---
title: "problem with dbus"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by RAJESHKSV on 2008-03-22
I HAD A PROBLEM WITH SERVICES...unknowingly I UNCHECKED system communication bus(dbus) .as a result many applets and services(such as hibernate, sleep and many more stopped working!!!

I found a soultion in one of ubuntu forums and i followed it but its not working completely .... as I entered

sudo /etc/init.d/dbus start

and Then run services-admin and enabled the System Communication Bus (dbus)

thn its fine,but it is only upto that session.!!!!!

When I restart my system , services window is opening(dbus is also in checked state) but still some services like hibernate,sleep are not working...Also the window

"Internal error:failed to initialise hal"

is still coming after every reboot...so oneday i found myself a solution..

Everytime I switch on my lap, I  stop the system communication bus(dbus)i.e.,uncheck it , and restart it again(through the above command from terminal)

...then hibernate and sleep are working...but Isnt there a complete solution to this problem????I think due to this in recent times my lap is being stucked very often...It became very slow...(ofcourse config is very good del vostro 1500 model 2gb ram ;120gb harddisk;1.6ghz processor)..so plz help ,its very annoying ...............................


plz tell me wt 2 do??:(

---

### Post by p_quarles on 2008-03-22
Can you post the output of this terminal command?:
```
ls /etc/rc2.d/*dbus
```

---

### Post by RAJESHKSV on 2008-03-22
/etc/rc2.d/S50dbus

---

