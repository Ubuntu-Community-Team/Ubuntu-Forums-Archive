---
title: "I Cant register lib libfaad2.dll in winXP prof sp3"
date: 2011-11-12
forum: Any Other OS
---

### Post by ivanhoe75 on 2011-11-12
This lib must be registered with command: 
regsvr32 c:\windows\system32\libfaad2.dll    but I see message "application cant be executed because of it is wrongly configured"
What to do?

---

### Post by qyot27 on 2011-11-13
What are you trying to do exactly?  I can't think of anything that uses FAAD2 where you have to register the actual .dll - typically what you have to register are .ax files or just tell the program that needs it where the .dll is.

---

### Post by ivanhoe75 on 2011-11-16
Awave studio 10.4

---

### Post by qyot27 on 2011-11-16
Quoted directly from the site for that software:
[http://www.fmjsoft.com/fmt/aac.htm](http://www.fmjsoft.com/fmt/aac.htm)

> To read .AAC files, you need to get hold of a copy of the DLL version of the open source 'FAAD 2' decoder and copy the file 'libfaad2.dll' **into the directory where you installed Awave Studio**.
(emphasis added)

---

