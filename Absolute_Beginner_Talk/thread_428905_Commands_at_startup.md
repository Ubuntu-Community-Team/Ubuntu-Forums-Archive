---
title: "Commands at startup"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ocho on 2007-04-30
I was wondering if there was an easy way to have Ubuntu run sudo commands at start up.

---

### Post by yabbadabbadont on 2007-04-30
If they are command line commands, there is no need for sudo.  Just add them to /etc/rc.local and they will be the very last thing run during boot up.

---

### Post by jfinkels on 2007-04-30
> **ocho said:**
> I was wondering if there was an easy way to have Ubuntu run sudo commands at start up.

You will always have to enter your password if you want to use sudo with a command, just remember that.

You can make a script, make it executable, then add it to startup programs under "System > Preferences > Sessions". your script might look something like this:
```

#!/bin/bash

sleep 10 && gksudo gedit

```
or whatever program you want to run. The sleep statement is in there so that the program won't run until your desktop is all done loading up.

Here's some more information on gksudo: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by ocho on 2007-04-30
Amazingly quick reply! Yes, that's exactly what I want to do.

Thanks a lot.

---

