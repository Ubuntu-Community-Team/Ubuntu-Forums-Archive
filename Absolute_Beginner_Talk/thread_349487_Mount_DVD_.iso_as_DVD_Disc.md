---
title: "Mount DVD .iso as DVD Disc"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by gidra on 2007-01-30
How do you mount a DVD .iso so that is recognised by the system as a DVD disk ? What i mean is that when i go to movie player there i want an option under Movie to Play Disk "name of .iso film". In other words it would seem that i have an other phsyical dvd drive. Thanks for any advice.

---

### Post by NESFreak on 2007-01-30
> **gidra said:**
> How do you mount a DVD .iso so that is recognised by the system as a DVD disk ? What i mean is that when i go to movie player there i want an option under Movie to Play Disk "name of .iso film". In other words it would seem that i have an other phsyical dvd drive. Thanks for any advice.

see [http://www.ubuntuforums.org/showthread.php?t=276743](http://www.ubuntuforums.org/showthread.php?t=276743)

NESFreak

---

### Post by gidra on 2007-01-30
can you give me the link again please cause it's giving me this 

"No Thread specified. If you followed a valid link, please notify the administrator"

---

### Post by taurus on 2007-01-30
Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop **filename.iso** /mnt/iso
xine dvd://mnt/iso
```

---

