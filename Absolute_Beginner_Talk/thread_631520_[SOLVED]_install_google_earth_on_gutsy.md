---
title: "[SOLVED] install google earth on gutsy"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Fanin on 2007-12-04
I'm trying to install Google Earth for Gutsty and so far i've tried this

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

and it won't work :confused:
if there is something wrong with the code please do tell

---

### Post by sethvath on 2007-12-04
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by SpacePilot on 2007-12-04
Try with:

wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
chmod 755 GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin

---

### Post by Dr Small on 2007-12-04
> **SpacePilot said:**
> Try with:

wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
+1
That is the way to go ;)

---

### Post by Fanin on 2007-12-04
thanks.. runs great :)

---

