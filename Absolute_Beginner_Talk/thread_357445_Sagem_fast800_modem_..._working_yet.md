---
title: "Sagem fast800 modem ... working yet ?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by its_jon on 2007-02-09
hi.

The last time I posted on this forum was September 2005 when I was struggling to get my internet connection working with my Sagem fast800 USB modem.

The Sagem Fast800 modem was supplied in vast quantities in the UK with Tiscali internet broadband signups.

Back then Ubuntu did not support the modem and despite much help from this forum I gave up trying after days of unsuccessful attempts typing in weird stuff into the box I had no understanding of.

Anyway its now well over a year since and I was wondering if Ubuntu supports this modem yet.  If so, Im ready to reformat. :)

thanks.

---

### Post by Stemp on 2007-02-09
Look at this : [EagleUsb]("https://help.ubuntu.com/community/UsbAdslModem/EagleUsb")

---

### Post by its_jon on 2007-02-09
I see it,
I read it,
Still struggling to understand.

So.... what version of Ubuntu works with the drivers... and is this a recent fix, or just the same stuff I tried to get working the last time.

thanks

---

### Post by cbudden on 2007-02-09
What version of ubuntu are you running at the moment ?

```

cat /etc/issue

```

You would be better off investing in a ethernet router than using a USB modem really.

---

### Post by its_jon on 2007-02-09
none.... thinking of trying it again... but just want to be sure of getting a net connection before I start... so I presume picking the right Ubuntu release is important.

---

### Post by Stemp on 2007-02-09
For Edgy (i386 only) :

download and save (on a usb key or somewhere else) these 2 packages 
[http://perso.orange.fr/j.m.e/ueagle-data_1.1-0ubuntu0_all.deb](http://perso.orange.fr/j.m.e/ueagle-data_1.1-0ubuntu0_all.deb)
[http://perso.orange.fr/j.m.e/installemodem_0.0.2-0ubuntu2_i386.deb](http://perso.orange.fr/j.m.e/installemodem_0.0.2-0ubuntu2_i386.deb)

For Dapper (i386) :
[http://perso.orange.fr/j.m.e/installemodem_0.0.1-0ubuntu7_i386.deb](http://perso.orange.fr/j.m.e/installemodem_0.0.1-0ubuntu7_i386.deb)

For Dapper (amd64):
[http://perso.orange.fr/j.m.e/installemodem_0.0.1-0ubuntu8_amd64.deb](http://perso.orange.fr/j.m.e/installemodem_0.0.1-0ubuntu8_amd64.deb)

When these packages are installed go to Menu, System, Administration, Internet ADSL

Source Ubuntu-fr forum : [http://forum.ubuntu-fr.org/viewtopic.php?pid=661417#p661417](http://forum.ubuntu-fr.org/viewtopic.php?pid=661417#p661417)

---

