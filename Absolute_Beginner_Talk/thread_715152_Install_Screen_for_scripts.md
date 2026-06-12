---
title: "Install Screen for scripts"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by czd2002 on 2008-03-04
How do i install screen? 
I am  trying to make a script called server.sh with this in it
#!/bin/sh
echo "Starting Cs:Source Server"
sleep 1
screen -A -m -d -S css-server ./srcds_run -console -game cstrike +map de_dust +maxplayers 16 -autoupdate

plz help.

---

### Post by Crooksey on 2008-03-04
```

$ sudo apt-get install screen
```

---

### Post by czd2002 on 2008-03-04
thank you worked great

---

