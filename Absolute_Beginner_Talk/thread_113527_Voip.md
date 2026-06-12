---
title: "Voip?"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-06
Hey.

Just wanted to know if there's any kind of software for Ubuntu/Linux that lets me make a call to an actual phone number - Like Skype, but, to an actual land line phone number?

Thanks

---

### Post by etc on 2006-01-06
Skype, PhoneGaim, and Gizmo all can

---

### Post by martinjanson on 2006-01-06
With skype you can have a landline numbers for the countries but NOT limited to Sweden, England, USA

You just have to pay some fee for that.

apt-get install skype

---

### Post by Jimmey on 2006-01-06
> james@ubuntu:~/Desktop$ sudo dpkg -i skype_1.2.0.18-1_i386.deb
Selecting previously deselected package skype.
(Reading database ... 59197 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.18-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
james@ubuntu:~/Desktop$


How'd I fix this?

---

### Post by martinjanson on 2006-01-06
Seems as the .deb file is foobared,, do check [https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

That worked for me, just tested

---

### Post by cjm5229 on 2006-01-06
Install it with Automatix, It will probably have some other things you will find useful also. Customization Tips & Tricks, right on top, and Don't forget to thank Arnieboy. 
Carl

---

### Post by dcast on 2006-01-06
that just means that it depends on those files install those and it will be fine

---

