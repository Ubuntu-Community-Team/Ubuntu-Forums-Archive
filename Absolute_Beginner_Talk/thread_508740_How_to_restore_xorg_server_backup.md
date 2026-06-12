---
title: "How to restore xorg server backup"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2007-07-24
Ok I messed with the xorg file and have realy messed it up but I made a back up like I was suposed to,so could you please tell me how to restore the backup file I made.

---

### Post by mikewhatever on 2007-07-24
Suppose the backup file is xorg.conf_backup and it is in /etc/X11/. 
> sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by Rocket2DMn on 2007-07-24
Get to a terminal and type
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
This assumes xorg.conf.backup is the name of your backup file.
Then you can reload the GUI with
```
/etc/init.d/gdm start
``` for the login screen, I believe, or
```
startx
``` to start the X-server running on your current terminal login.

---

### Post by Foxmike on 2007-07-24
Where is the backup located?

---

### Post by Cypher on 2007-07-24
```

sudo cp /etc/X11/<back up xorg.conf file> /etc/X11/xorg.conf

```

---

### Post by Foxmike on 2007-07-24
> **Cypher said:**
> ```

sudo cp /etc/X11/<back up xorg.conf file> /etc/X11/xorg.conf

```
How to make 2 posts look like one. :D

---

