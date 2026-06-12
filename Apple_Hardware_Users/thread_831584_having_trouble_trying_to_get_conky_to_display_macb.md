---
title: "having trouble trying to get conky to display macbook fanspeed and temp"
date: 2008-06-17
forum: Apple Hardware Users
---

### Post by dustynus on 2008-06-17
So I have the fanspeed and temp showing up with the gnome sysmonitor applet.
Can't seem to figure out how to get conky to show the same info.

Anyone done this before?

Thanks

:guitar:

---

### Post by ad_267 on 2008-06-18
You need to do this with lm-sensors, although it's interesting you can do this with the gnome system monitor as I can't.

You need to run:
```
sudo apt-get install lm-sensors
sudo lm-sensors detect
```

You will also need to restart after this as it loads kernel modules. Then you can run the command "sensors" to see all the information you can get.

From the output of sensors you need to figure out what variable to use from the conky variables page ([http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)). If you get stuck then post the output here.

Edit: I should add that I haven't done this with a mac but I assume it will work the same.

---

### Post by Kooothor on 2008-09-09
> **dustynus said:**
> So I have the fanspeed and temp showing up with the gnome sysmonitor applet.
Can't seem to figure out how to get conky to show the same info.

Anyone done this before?



Yes,

try :
```
${color white}${exec sensors | grep 'RPM'}
${exec sensors |grep temp | cut -c1-16}
```

Of course, you need to have lm-sensors installed.
And on a macbook, the correct module to load is "coretemp"
but you can't, it's not available.

bye.

---

