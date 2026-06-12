---
title: "Internet connection using LiveCD"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Pandabuntu on 2007-03-19
Hi,

I have downloaded and burned the Ubuntu LiveCD. It boots fine and seems to be a very nice choice of OS - but for some reason or other I seem to have a problem with connection to the internet. I am using an ethernet connection which works fine from my windows xp platform. Apparently Ubuntu do detect the ethernet as active but it doesn't allow me to browse the www.
Isn't it not possible to use the internet from the LiveCD or is there some setup that I have to do?
The connection is setup to automatically get an IP address when the ethernet cable is connected (from DHCP) - this is the same setup as I have in windows and should work...or?

Thanks for your help!

---

### Post by AtrejuT on 2007-03-19
it should work indeed, I think.
what happens if you open a terminal and enter

```

ifconfig

```

you should also try
```

sudo dhclient

```

---

### Post by oilchangeguy on 2007-03-19
don't know if this will make a difference. but turn off (unplug) your cable modem for about a minute and turn it back on. probably should restart the computer as well.

---

### Post by kingjimbob on 2007-03-19
Newbie here: I have a similar problem to this, yet to find the cause in either Ethernet or wireless. Tried manual config as well. But if i do have any luck i will let you know.

---

### Post by zvacet on 2007-03-19
[http://ubuntuforums.org/showthread.php?t=387679]("http://ubuntuforums.org/showthread.php?t=387679")

---

