---
title: "tar.gz error"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-09-22
Got as far downloading  'garmin_gps-0.31a.tar.gz' to the desktop, when i attempt extracting it i get this:
tar:garmin_gps-0.31a.tar.gz : Cannot open : no such file or directory
tar:Error is not recoverable :exiting now
tar:Child returned status 2
tar:Error exit delayed from previous errors

This file is drivers for gps.should i delete & try fresh download.

---

### Post by Bachstelze on 2007-09-22
If the file is on your desktopp, you must do

```
cd ~/Desktop
```

before. If you don't, the shell is searching the file in your home dir and obviously doesn't find it.

---

### Post by Maestro23 on 2007-09-22
Need to change to Desktop directory.

> cd /home/username/Desktop (Capital D)

Then run your tar command.

---

### Post by jon zendatta on 2007-09-22
Thanks Maestro Hymntolife, you saved my headache:)

---

