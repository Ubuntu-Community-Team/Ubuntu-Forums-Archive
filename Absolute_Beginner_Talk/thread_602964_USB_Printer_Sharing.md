---
title: "USB Printer Sharing"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by iain010100 on 2007-11-04
Hello,

Is it possible to connect a USB printer to my Ubuntu PC then share it over a network so the other PCs (Vista and XP) can print?

This seems like it might be a common question so forgive me if it's been answered 100 times, but I've not found anything relevant on Ubuntu forums.

-- Iain

---

### Post by houstonbofh on 2007-11-04
Yes.  However, you first have to decide if you want to share it with CUPS or SAMBA.  Since you mentioned a healthy Windows bias, you might want to look into SAMBA.  But it ain't easy.  In CUPS you can share more intuitively, but it is less supported.

---

### Post by daengbo on 2007-11-04
I believe SAMBA is set up to share printers from CUPS by default if both are installed.

He'll need to check the "Share Printer" checkbox in the System -> Administration -> Printing dialog, and install [Samba]("apt:samba").

Good luck.

---

### Post by houstonbofh on 2007-11-05
Please not that samba is not trivial.  Some links to get you going...
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)
[https://help.ubuntu.com/community/MythTV/Install/Server/WhatNext/Samba](https://help.ubuntu.com/community/MythTV/Install/Server/WhatNext/Samba)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/community/SettingUpSambaPDC](https://help.ubuntu.com/community/SettingUpSambaPDC)

This is more than you need.  I doubt you will also set up a MythTV box or a PDC right away. :)  But there are some good pointers and links in here.  Good luck.

---

