---
title: "How to restart samba"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by acl123 on 2007-12-23
Hi, I am trying to restart samba after editing smb.conf, but the suggested way of '/etc/init.d/samba restart' does not work. The file /etc/init.d/samba does not exist.

Does anyone know how I can restart it without restarting Ubuntu?

---

### Post by reckless2k2 on 2007-12-23
from the terminal type:

```
sudo /etc/init.d/samba restart
```

---

### Post by Rocket2DMn on 2007-12-23
Try System->Administration->Services then uncheck/check the box for Samba.
You can also use System->Administration->Bootup Manager

---

### Post by acl123 on 2007-12-23
> **reckless2k2 said:**
> from the terminal type:

```
sudo /etc/init.d/samba restart
```

Woh thanks for the reply... but please read posts before replying - not just the header... or maybe you're one of those "forum bots" that people were talking about yesterday :P

---

### Post by acl123 on 2007-12-23
OK I worked it out - I didn't realise you can have a smb.conf without samba being installed. When I started System->Administration->Shared Folders it offered to install samba for me.

---

### Post by reckless2k2 on 2007-12-23
there you go rocket scientist. hahaha. i do admit that i half read it but if it didn't work via command line restart.....there was that kinda issue. hahaha

---

### Post by PinkFloyd102489 on 2007-12-23
you can also replace "restart" with "reload" to rehash the configuration file without shutting down and starting the daemon.

---

