---
title: "[SOLVED] How to connect to MOdem?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by My_Ausweis on 2007-12-12
How to connect to telephone modem ?

Ubuntu has detected my modem :

HSF Connexant

But when I tried to choose dial up using modem ppp0, it didn't work, password, user name and telephone number already filled in and no DNS required and 

I already click Restricted Hardware Manager, but found nothing

"There is no hardware for Restricted Manager"

anyone know how to solve it ?

---

### Post by zvacet on 2007-12-13
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6")

---

### Post by My_Ausweis on 2007-12-21
I tried to use sudo pppconfig

I already created account, with peer but when i tried run with instruction pon

it didn't work and shown "unrecognized /dev/modem"

Any body can help me ?

Thx

---

### Post by nowshining on 2007-12-21
go to properties and select activate and to de-activate u uncheck it, u can go to my website for a patched version of gnome-ppp which fixes a bug where the window won't minimize but connects, go into setup and press detect - last tab to do checks on whether to minimize or dock to notification area..right-click it to connect..

site is in my sig.

---

### Post by My_Ausweis on 2007-12-23
I tried to use bug fix for gnome-ppp but it still not work.

I tried use any alternative by putting an internet connection (shown as telephone equipment) in the panel, but when i right click the mouse the active and deactive writing in gray color, I click the Modem using Network , i already tried to change from COM1-COM4 (Internal Modem) and /dev/modem but nothing happen, any one know how to solve it ?

Thx

L.M

---

### Post by nowshining on 2007-12-23
what didn't work exactly? did it not start-up? errors? gnome-ppp is what i mean?

---

### Post by My_Ausweis on 2007-12-26
Just Active and deactive in gray color(In active condition), but hardware detected as Connexant HSF Modem

That i confuse

---

### Post by honda on 2008-01-04
The conexant HSF modem requires a closed driver that wasn't even free as in beer, but since Dell started preinstalling ubuntu, they also made available a driver for that modem that anybody can dowload from the Dell site.
[https://help.ubuntu.com/community/DialupModemHowto/Conexant]("https://help.ubuntu.com/community/DialupModemHowto/Conexant")

Lately Dell also made available a driver for ubuntu 7.10 :
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver")

---

