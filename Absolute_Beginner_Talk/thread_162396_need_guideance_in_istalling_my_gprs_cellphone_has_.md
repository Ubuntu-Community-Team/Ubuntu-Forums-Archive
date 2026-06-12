---
title: "need guideance in istalling my gprs cellphone has a modem"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by drking on 2006-04-18
got a motorola c330 cell phone that i use to browse the internet and i can't get the modem to work in ubuntu need a step by step help

---

### Post by Sandlst on 2006-04-18
Have you looked at [this]("http://tips.linux.com/article.pl?sid=05/08/25/188224&tid=100")?
step by step: (type enter after each terminal command)
Download GPRSEC_300_Beta_01-10_Install.tar.bz2 from the site.  Double click to open, select !300_beta01_10 and click 'extract' in the top of the window.  Choose to extract to home.  Now open a terminal (Applications/Acessories/Terminal) type in ```
cd \!300_beta01_10/

``` then Enter ```
sudo apt-get install libgtk2-trayicon-perl
```  then ```
sudo sh INSTALL.sh
``` go through the wizard, select both boxes when they come up (for stuff to set up/install files.  Once its finished run from a terminal with 'gprsec'.  Good luck, post back if you have any problems.

---

