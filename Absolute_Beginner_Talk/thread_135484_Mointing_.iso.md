---
title: "Mointing .iso"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by OkydOky on 2006-02-23
How would one mount a .iso CD image in ubuntu?
Is is Build in? or is a program needed?

---

### Post by joshuapurcell on 2006-02-23
```
sudo mount -o loop -t iso9660 /path/to/ISO /path/to/mountpoint
```

---

### Post by heimo on 2006-02-23
Like this:
```
sudo mount -o loop -t iso9660 dapper-live-i386.iso mountpoint
```[I]
mountpoint[/I] needs to be existing directory. I have no idea if this is possible from GUI.

---

### Post by Marshall2day on 2006-02-24
I know there is a script for nautilus somewhere on this forum that creates a mountpoint and mounts the iso automatically.

---

### Post by joshuapurcell on 2006-02-24
[QUOTE=Marshall2day]I know there is a script for nautilus somewhere on this forum that creates a mountpoint and mounts the iso automatically.[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)

---

