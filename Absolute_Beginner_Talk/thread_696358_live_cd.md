---
title: "live cd"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-02-13
okay when i try to install build-essentials it asked me to insert the live cd. well the problem is that i dont have exact live cd or any cds to burn a ubuntu live cd anyway i can get around it?

---

### Post by AsoSako on 2008-02-13
Go to Software Sources and remove the CD as a source.

---

### Post by HappyFeet on 2008-02-13
in terminal,
```
gksudo gedit /etc/apt/sources.list
```
put a "#" (without quotes) in front of the line that says deb cdrom. it will be one of the first lines you will see. then save and do
```
sudo apt-get update
```

---

