---
title: "scanner not working"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Big_Kiwi on 2007-06-07
Hi all

Need some help again please. I have a canon LiDe20 scanner but can not get it to work, have tried to use it with Xsane but the scanner dose not work or XSane dose not reconize it, I wounder if maybe I did not install the drivers correctly (WHAT DRIVERS0 I thought Ubuntu might find it automaticaly  as it did my printer, any Ideas on how I can get my scanner working

---

### Post by dbbolton on 2007-06-07
> **Big_Kiwi said:**
> Hi all

Need some help again please. I have a canon LiDe20 scanner but can not get it to work, have tried to use it with Xsane but the scanner dose not work or XSane dose not reconize it, I wounder if maybe I did not install the drivers correctly (WHAT DRIVERS0 I thought Ubuntu might find it automaticaly  as it did my printer, any Ideas on how I can get my scanner working
go to [http://www.sane-project.org/](http://www.sane-project.org/) and see if your scanner is listed under supported devices.

---

### Post by Big_Kiwi on 2007-06-08
Yes it is listed but not working under Xsane any Ideas

---

### Post by PhilJ on 2007-06-08
have you edited the relevant conf files in /etc/sane.d . look for the conf files for your make and uncomment the line that contains your scanner. In my case they were Mustek.conf mustekpp.conf and dll.conf

Philj

---

### Post by WW on 2007-06-08
You might be affected by [Bug #85488]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85488")

---

