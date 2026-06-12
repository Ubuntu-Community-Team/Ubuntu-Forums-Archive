---
title: "cd/dvd image"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by phuchungbhutia on 2007-10-25
is there a way to read cd/dvd images like .iso in ubuntu ...

and also is there some way to open phone memory (stick pro).....

---

### Post by mikeyphi on 2007-10-25
> **phuchungbhutia said:**
> is there a way to read cd/dvd images like .iso in ubuntu ...

and also is there some way to open phone memory (stick pro).....

Q1. Burn to disc and then boot from disc
Q2. Don't know!

---

### Post by marco123 on 2007-10-25
With my phones I just plug them in and they come up as removable drives.

---

### Post by sisco311 on 2007-10-25
you must create a folder and mount the iso file.
open a terminal and type:
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop **file.iso** /media/iso/
```file.iso is the name of the iso file.
the content of the iso file will be in /media/iso folder

---

### Post by julian67 on 2007-10-25
[ HOWTO: Nautilus Script to mount .iso files]("http://ubuntuforums.org/showthread.php?t=87369")

also possible in thunar:

[ HOW-TO: Mount ISO script for Thunar]("http://ubuntuforums.org/showthread.php?t=380602")

[IMG]http://img339.imageshack.us/img339/9748/screenshot3tw2.png[/IMG]

---

