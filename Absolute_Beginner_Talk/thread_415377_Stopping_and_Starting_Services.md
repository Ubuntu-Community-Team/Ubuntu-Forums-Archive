---
title: "Stopping and Starting Services"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by arsenik on 2007-04-20
I try the command:

Service openvpn Start

and its not working.

Is there a different command in ubuntu to do this?

---

### Post by arsenik on 2007-04-20
i used /etc/init.d/openvpn start and that worked, but is there not a service openvpn start command?

---

### Post by AtrejuT on 2007-04-20
```

The program 'service' can be found in the following packages:
 * debian-helper-scripts
 * sysvconfig
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: service: command not found

```
so I'd try installing debian-helper-scripts
```

sudo apt-get install debian-helper-scripts

```

---

### Post by arsenik on 2007-04-20
thx m8, I'm going to try it out now.

---

