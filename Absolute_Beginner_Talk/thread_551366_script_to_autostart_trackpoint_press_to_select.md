---
title: "script to autostart trackpoint press to select"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by cvaty on 2007-09-15
this script makes the ibm trackpoint (red dot) select on tapping
```

#!/bin/bash
       if [ "$1" = "1" ]; then
               echo "Turning on tap on TrackPoint"
               echo -n 1 > /sys/devices/platform/i8042/serio1/press_to_select
               exit 0
       fi
       if [ "$1" = "0" ]; then
               echo "Turning off tap on TrackPoint"
               echo -n 0 > /sys/devices/platform/i8042/serio1/press_to_select
               exit 0
       fi
       echo -n "Tap status: "
       cat /sys/devices/platform/i8042/serio1/press_to_select

```

how does someone go about getting something like this to run automatically at startup?

---

### Post by black_ice on 2007-09-15
just add it to /etc/init.d

---

### Post by cvaty on 2007-09-15
added it to the folder
but its not starting

... any ideas?

sesions manager maybe?

---

### Post by wahoobob on 2008-02-24
As a newcomer to Linux I would appreciate someone would give a detailed explanation of how to get the trackpoint working completely  -  I know it would help me to get all this done if the commands and where to put them (how to put them) were given.

Thanks for your patience...:confused:

---

### Post by glennric on 2008-02-24
Just adding the script /etc/init.d will not make it run on startup.  You also have to make a link to it in a run level.  For example, if you want to make the script run upon entering runlevel 2 (the default) type the following in a terminal:
```
sudo update-rc.d script-name start 60 2 .
```
where 60 refers to the order that the script will be run in relation to the other scripts.  Don't forget the "." at the end of the line.  It won't work without that.  After doing this you can look in /etc/rc2.d/ and you will see a link named 60script-name to the file you put in /etc/init.d/.
To change the runlevel that the script starts in change the 2 above.  If you replace the 2 with an S the script will be run when the runlevel is changed (for instance when you start the computer and the runlevel changes from none to 2).
To stop the script from loading at startup type
```
update-rc.d -f script-name remove
```

By the way, I don't know anything about trackpoint so I can 't help you there.

---

