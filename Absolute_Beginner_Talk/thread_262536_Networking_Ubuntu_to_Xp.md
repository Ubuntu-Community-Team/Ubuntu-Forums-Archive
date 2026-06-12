---
title: "Networking Ubuntu to Xp"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Benji77 on 2006-09-21
hello there

i have networked a Ubuntu desktop pc to a xp one and i can see the Ubuntu desktop in network neighborhood on my xp machine but cant get into the ubuntu  machine to root files or whatever, because it asking me for a password but i havent passworded anything please help

---

### Post by [S|G] on 2006-09-21
How did you network it? Samba? And can't you access Ubuntu from your XP computer? Or can't you access your XP box with your linux?

---

### Post by Frak on 2006-09-21
Samba?

---

### Post by Benji77 on 2006-09-21
yes i used samba

---

### Post by Tux Aubrey on 2006-09-21
The same issue drove me nuts for almost a week.

Despite probably fifty attemps at setting Unix and Ubuntu passwords, none were acceptable.

I did eventually find a way to do it - using guest user = ok in the smb.conf file (as discussed in [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)) but I feel that this is an unacceptable workaround on a wireless network on which I can't use encryption.  I actually wanted password protection but it did not work.

A really good "Samba Ubuntu WinXP home networking How To" would be great - or perhaps a GUI.

Hope this helps. 

Aubrey

---

### Post by tagra123 on 2006-09-21
Heres a good link for samba server setup as well as many other things.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

This link should answer your questions though.

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

