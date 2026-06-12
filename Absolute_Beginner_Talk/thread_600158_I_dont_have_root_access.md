---
title: "I dont have root access"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Bob_12 on 2007-11-02
I want to copy a map pack to my Nexuiz folder but it says that I cant copy there because I dont have access because its root. What do I do?

---

### Post by BentFX on 2007-11-02
> **Bob_12 said:**
> I want to copy a map pack to my Nexuiz folder but it says that I cant copy there because I dont have access because its root. What do I do?

use...

sudo *<command>*

for a single command, or...

sudo -s [return]

for multiple commands.
When it asks for a password, it wants yours, not root's

Hope that works.

---

### Post by aysiu on 2007-11-02
> **Bob_12 said:**
> I want to copy a map pack to my Nexuiz folder but it says that I cant copy there because I dont have access because its root. What do I do?
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Arthur Archnix on 2007-11-02
You would do sudo cp /path_to_map_pack /path_to_destination_folder. So, say you mappack is on your desktop, and your destination folder is /bin.. it might look something like this
```
sudo cp ~/Desktop/mappack/coolmap /bin/netuiz/maps/
```

You may need to create the destination directory if it doesn't already exist, using sudo mkdir, or else use mv instead of cp

---

