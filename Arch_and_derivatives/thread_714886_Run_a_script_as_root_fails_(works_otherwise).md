---
title: "Run a script as root fails (works otherwise)"
date: 2008-03-04
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-03-04
In my /etc/acpe/handlers.sh file I have it set so that when I close the lid it suspends and is locked with gnome screensaver with this
```

#!/bin/bash

sleep 1 &&
gnome-screensaver-command -l &&
sleep 3 &&
sudo pm-suspend --quirk-s3-bios --quirk-s3-mode &&

```

But of course it doesn't work. If I run it as a normal user, it works. So I figured it was because acpi runs as root, so I ran the script as root and got:

```

** Message: Failed to connect to the D-BUS daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

What would be wrong? I've tried the script with and without the sudo and it is set up for no password.

---

### Post by Crooksey on 2008-03-04
Take the sudo command out of the script and just run it as root.

---

### Post by PurposeOfReason on 2008-03-04
I tried it again, no sudo, actually a whole new script with different permissions, still nothing.

---

### Post by PurposeOfReason on 2008-03-04
Got it to work with xscreensaver so I'm not too bothered. But if someone could help me theme it with this, I'd be grateful. When I download the tar and apply the patch, it works but when I compile it says I don't have bc, which I obviously do because arch comes with it.

[http://www.swanson.ukfsn.org/xss/](http://www.swanson.ukfsn.org/xss/)

EDIT - Got past that, but there isn't a path for xscreensaver 5..05. Anyone know where an archive is so I can get an older version?

---

