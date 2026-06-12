---
title: "firefox issue with flash"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by l.j. on 2006-11-04
Hi all i just finished loading the edgy distro the upgrade from 6.06 didnt go well so just did a clean install anyhow i laoded a web page that required the flash plugin and said click here to install the process went right through now if my browser loads anything with flash it crashes any ideas how to reverse this:(

---

### Post by bsell on 2006-11-05
Firefox 1.5.0.x crashed on Flash pages in 6.06 as well. I upgraded to 6.10 and Firefox 2.0 crashes on Flash pages too. Flash plugin for Firefox is installed, but it only works in Epiphany.

---

### Post by MasterOfDisaster on 2006-11-05
Firefox works fine for me on 6.10, and was fine on 6.06.

How did you install flash, from the website or through EasyUbuntu, Synaptic or such?

---

### Post by Chayak on 2006-11-05
You need to go into your xorg.conf and change your default bitdepth to 24

---

### Post by bsell on 2006-11-05
I installed through Synaptic. I just edited the xorg.conf file and rebooted. Firefox now displays Flash and doesn't crash.

THX!

---

### Post by l.j. on 2006-11-21
Thanx yall the 24depth was the answer appreciate the help,
Im an it administrator for a school district (Micro$oft shop) but it pays the bills, i started using linux and UBUNTU about 3mos ago and wow reminds me why i fell in love with computers :)

---

