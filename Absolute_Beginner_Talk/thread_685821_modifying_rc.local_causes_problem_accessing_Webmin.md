---
title: "modifying rc.local causes problem accessing Webmin"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Shiva-Shinken on 2008-02-02
I modifed the /etc/rc.local file so as to start a Counter Strike game server at boot, it now looks like this ```

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

cd /halflife/hlds_l

./hlds_run -game cstrike -insecure -nomaster +sv_lan 1 +maxplayers 18 +map cs_assault

exit 0

```

Well, the game server is starting fine, but for some reason this entry is causing me problem accessing Webmin, as if Webmin is not starting.  As soon as I remove the 2 active lines and reboot then Webmin works fine.  What gives?

CC

---

### Post by amingv on 2008-02-02
Maybe check that Webmin and the game server are using different ports...

---

### Post by dcstar on 2008-02-03
> **Shiva-Shinken said:**
> I modifed the /etc/rc.local file so as to start a Counter Strike game server at boot, it now looks like this ```

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

cd /halflife/hlds_l

./hlds_run -game cstrike -insecure -nomaster +sv_lan 1 +maxplayers 18 +map cs_assault

exit 0

```

Well, the game server is starting fine, but for some reason this entry is causing me problem accessing Webmin, as if Webmin is not starting.  As soon as I remove the 2 active lines and reboot then Webmin works fine.  What gives?

CC
Get rid of the "cd" and try:
```
/halflife/hlds_l/hlds_run -game cstrike -insecure -nomaster +sv_lan 1 +maxplayers 18 +map cs_assault **&**
```

---

