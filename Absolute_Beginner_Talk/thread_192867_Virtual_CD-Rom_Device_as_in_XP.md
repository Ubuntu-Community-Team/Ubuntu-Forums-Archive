---
title: "Virtual CD-Rom Device as in XP"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by vinodis on 2006-06-09
How can I map an .ISO file as a CD-ROM drive ( or mount letter ) in Ubuntu?

TIA

---

### Post by frodon on 2006-06-09
Using these command lines : ```
sudo modprobe loop
sudo mount *file.iso* /media/cdrom0 -t iso9660 -o loop
```I assume that you have a cdrom drive called cdrom0 under /media, i think it should be the case.

---

### Post by vinodis on 2006-06-09
Oh. Thank you very much. You saved me a lot of problems having to burn my ubuntuplus cd from an .ISO on my usb drive. 
Thanks again!

---

