---
title: "rc.local doesn't work"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by provisional_idiot on 2008-03-02
so i want to run conky a startup, but rc.local doesn't seem to run.... Any help??

-rwxr-xr-x   1 root   root       536 2008-03-02 14:47 rc.local

```
#!/bin/bash
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

DELL_355_MODULE=""
DELL_355_MODULE=`sudo lsusb -v | grep "ID.*413c:8126"`
if [ -n "$DELL_355_MODULE" ] ; then
         hciconfig hci0 reset
fi
conky
modlist=`lsmod | grep snd_hda`
[ -z "$modlist" ] && modprobe snd_hda_intel

exit 0


```

---

### Post by glennric on 2008-03-02
This is not the way to run conky at startup.  You should add it in System->Preferences->Sessions

---

### Post by provisional_idiot on 2008-03-02
i see.. any explanation for why rc.local doesn't work??

---

