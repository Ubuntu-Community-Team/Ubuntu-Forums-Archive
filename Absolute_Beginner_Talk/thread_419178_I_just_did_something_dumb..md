---
title: "I just did something dumb."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by SSB on 2007-04-22
I disabled the fglrx drivers in the restricted drivers manager hoping i could reenable it or something to fix some issues i was having. I rebooted and now I get an error screen saying the GUI couldn't start up. How can I reinstall these drivers through the recovery mode?

---

### Post by NoobConvert on 2007-04-22
I had a simliar problem getting the desktop to load so I used ctrl + alt+ F1 to launch terminal after the boot failed.  Then use normal apt-get commands to re-install the fglrx drivers.

---

### Post by SSB on 2007-04-22
i know that much, but what's the normal apt-get command to do that?

---

### Post by nixclusive on 2007-04-22
The usual apt-get syntax for installing any package is:```
apt-get install <package-name>
``` If the package is already installed and you'd like to re-install it: ```
apt-get --reinstall install <package-name>
```

---

