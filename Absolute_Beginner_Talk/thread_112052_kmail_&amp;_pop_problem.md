---
title: "kmail &amp; pop problem"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Mis_Uszatek on 2006-01-03
I have installed kmail on Ubuntu(I'm using Gnome)

Configured all settings, click on send/receive, appears monit to insert password
and then...
appears info with :
"KMail - Error"
"Could not start process pop3."

Do I have to set pop daemon or something?

Evolution is working fine, but KMail not.

Best regards

---

### Post by thekiller on 2006-01-03
sudo apt-get install cyrus21-pop3d

then restart kmail, hopefully it should work

---

### Post by Mis_Uszatek on 2006-01-04
[QUOTE=thekiller]sudo apt-get install cyrus21-pop3d

then restart kmail, hopefully it should work[/QUOTE]

It didn't help.

Maybe it is because kmail is for KDE, and I am using gnome desktop, or maybe some misconfiguration in kmail, (evolution is working properly).

If anybody has any ideas, come on :)

---

### Post by ecaf on 2006-01-23
Hi!
Try to install "kdebase-kio-plugins", this helped for me, more information (in german) at [http://www.ubuntu-forum.de/artikel/4841/geloest-ubuntu-und-Kmail.html](http://www.ubuntu-forum.de/artikel/4841/geloest-ubuntu-und-Kmail.html)

---

### Post by bratliff on 2007-03-04
WHen I execute this command sudo apt-get install cyrus21-pop3d
The terminal gets to a point then will not go forward or accept keystrokes or mouse clicks.


ratliff

---

