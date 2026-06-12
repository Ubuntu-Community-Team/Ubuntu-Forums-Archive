---
title: "remove share pdf and printers/faxes?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by fondoo on 2008-02-11
i've successfully installed ubuntu server and setup samba server. does anyone know how i can remove the shared **pdf** and **printers and faxes**??

thanks!

---

### Post by nikoPSK on 2008-02-12
System -> Administration -> Printing might help you.

---

### Post by fondoo on 2008-02-13
i deleted PDF from System -> Administration -> Printing

do you know how i can remove _Printers and Faxes_??

thanks!

---

### Post by rkd on 2008-02-13
I'll admit that I don't know a lot about Samba, so this might not be the right answer. If "printers and faxes" is one of the items you see when browsing to the Samba system from another computer, I think you can get rid of it by editing the /etc/samba/smb.conf file. Find the part of the file that begins with "[printers and faxes]" and delete all the lines from that one up to just before the next line enclosed in "[" and "]".

Of course, make a copy of the file before doing this so you can put things back the way they were if this change causes problems.

The commands would be something like:```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
gksu gedit /etc/samba/smb.conf
```

---

