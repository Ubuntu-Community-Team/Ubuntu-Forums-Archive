---
title: "Bluetooth off on startup with 9.10"
date: 2010-03-10
forum: Apple Hardware Users
---

### Post by Lokesh123 on 2010-03-10
Hi,

by default Bluetooth is enabled on my Intel iMac with Ubuntu 9.10 (I think due to /etc/init.d/bluetooth script). 

I would like to disable it at startup w/o manualy disabling it on through the BT manager (which works, though). There are several posts already, but unfortunately many are open ended :(, or refer to config files that do not exist on my installation.

I want to change the default setting to "off" at startup, but the bluetooth manager in the panel should be able to turn it on when needed.

Any ideas?

Thanks,
Lokesh

---

### Post by linuxopjemac on 2010-03-10
I had the same problem as you, I fixed it like this:

add the following line to /etc/rc.local

```
rfkill block bluetooth
```

[http://mac.linux.be/phpBB3/viewtopic.php?f=13&t=55](http://mac.linux.be/phpBB3/viewtopic.php?f=13&t=55)

---

### Post by Lokesh123 on 2010-03-10
Greetings to Holland!

It works like a charm. Thanks a million. Here is my rc.local:

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

# Turn off BT at startup
rfkill block bluetooth

exit 0

Cheers
Lokesh

---

### Post by linuxopjemac on 2010-03-10
Greetings from a sunny Holland back to Lokesh123.
If you don't use BT, it only eats your battery for nothing...

---

### Post by Atilana on 2010-03-10
Hi, I had the same issue but fortunately i unistall the software and them re install again..

---

### Post by Michal77 on 2010-05-02
Works as charm on for me too.
M.

---

