---
title: "Setting up File Server using Samba"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by Robb on 2006-03-16
I've installed samba and created a shared folder. I can see the ubuntu system from from my windows machine on my network listed under the same domain but when I click on the ubuntu system to browse through any shared directories windows will prompt me for a username and password. Any username and password I use doesnt seem to work. Any ideas? I've tried the password of the user that created the share and even admin passwords for my domain and still no luck. Appreciate any help.
Thanks!

---

### Post by John.Michael.Kane on 2006-03-16
[http://www.oreilly.com/catalog/samba/chapter/book/index.html](http://www.oreilly.com/catalog/samba/chapter/book/index.html)
[http://www.samba.org/samba/docs/man/Samba3-HOWTO/](http://www.samba.org/samba/docs/man/Samba3-HOWTO/)
[http://www.linuxheadquarters.com/howto/networking/samba.shtml](http://www.linuxheadquarters.com/howto/networking/samba.shtml)

---

### Post by cb03BoilerUp on 2006-03-16
Are these liks up to date?  Little mention of WinXP, which has different networking capabilities of previous versions.

---

### Post by Robb on 2006-03-17
Thank you

---

### Post by John.Michael.Kane on 2006-03-17
cb03BoilerUp
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)
[http://hr.uoregon.edu/davidrl/samba.html](http://hr.uoregon.edu/davidrl/samba.html)

[http://xp-samba.linuxgod.net/Samba.php](http://xp-samba.linuxgod.net/Samba.php)
[http://www.linuxgod.net/docs/Samba-PDC-HOWTO.html](http://www.linuxgod.net/docs/Samba-PDC-HOWTO.html)

---

### Post by cb03BoilerUp on 2006-03-18
Thanks for the hekp.

---

### Post by MetalMusicAddict on 2006-03-18
[QUOTE=Robb]I've installed samba and created a shared folder. I can see the ubuntu system from from my windows machine on my network listed under the same domain but when I click on the ubuntu system to browse through any shared directories windows will prompt me for a username and password. Any username and password I use doesnt seem to work. Any ideas? I've tried the password of the user that created the share and even admin passwords for my domain and still no luck. Appreciate any help.
Thanks![/QUOTE]
You have to add users on the system *and* as a network user.

System-> Administration-> Users and Groups. Add your username (from your XP box) and give them a password here. ie: bob.
Then from a terminal type: **sudo smbpasswd -a *bob***. It will ask you to create a password. If I remember right the passwords can be different from each other.

---

### Post by cb03BoilerUp on 2006-03-19
Doesn't that just change the password for an already existing user?

---

