---
title: "Add terminal lines to startup"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by WUSB11 MY A**E on 2007-09-21
Right, every time I startup I need to type these lines into the terminal just to get the internet working, and it can be quite annoying:

```
sudo iwconfig wlan0 mode ad-hoc
sudo ifdown wlan0
sudo ifup wlan0
sudo route add default gw 192.168.0.1
```

Anyway, would it be possible to add these lines to startup or at least bung 'em all into a file so they all run at the click of a button (like with a windows batch file)

Thanks

---

### Post by kerry_s on 2007-09-21
try adding it to /etc/rc.local it runs as root.

**gksudo gedit /etc/rc.local**

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[B]iwconfig wlan0 mode ad-hoc
ifdown wlan0
ifup wlan0
route add default gw 192.168.0.1
[/B]
exit 0

---

### Post by amgat on 2007-09-21
Write a script. put it in the /etc/init.d/ directory.
Lets say you called it FOO. You then run

% update-rc.d FOO defaults

You also have to make the file you created, FOO, executable, using
```
$chmod +x FOO
```

You can check out
% man update-rc.d for more information. It is a Debian utility to install scripts. The option “defaults” puts a link to start FOO in run levels 2, 3, 4 and 5. (and puts a link to stop FOO into 0, 1 and 6.)

Also, to know which runlevel you are in, use the runlevel command.

---

### Post by WUSB11 MY A**E on 2007-09-21
> **kerry_s said:**
> try adding it to /etc/rc.local it runs as root.

**gksudo gedit /etc/rc.local**

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[B]iwconfig wlan0 mode ad-hoc
ifdown wlan0
ifup wlan0
route add default gw 192.168.0.1
[/B]
exit 0

That worked perfectly, thanks :D

---

