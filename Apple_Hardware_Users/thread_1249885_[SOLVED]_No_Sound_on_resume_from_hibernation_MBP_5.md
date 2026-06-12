---
title: "[SOLVED] No Sound on resume from hibernation MBP 5,3"
date: 2009-08-25
forum: Apple Hardware Users
---

### Post by amd-64 on 2009-08-25
Once I got the sound working on a MBP 5,3 by compiling the updated alsa modules, I found that sound no longer works after hibernation. 

Alsa needs to be suspended. I installed this code 

```
sudo gedit /etc/pm/sleep.d/45sound 

``` 

```

#!/bin/bash

if [ ! -x /sbin/alsa ]; then
        exit 0;
fi

case "$1" in
        hibernate|suspend)
                /sbin/alsa suspend
                ;;
        thaw|resume)
                /sbin/alsa resume
                ;;
        *)
                ;;
esac
exit $?

```

Save and make it executable

```

sudo  chmod 755 /etc/pm/sleep.d/45sound

```
Now sound should survive hibernation.

---

