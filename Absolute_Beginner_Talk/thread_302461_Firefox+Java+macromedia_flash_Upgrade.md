---
title: "Firefox+Java+macromedia flash Upgrade"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-18
I know this question is over asked.
I'm trying to upgrade my firefox to java and macromedia plugins. Should i go to a site that requires java and macromedia and click on download plugins or is there a safer way to do it. I dont want to lose my connection again so i'm trying to be carefull.
I need also to know how to reinstall firefox in case the upgrading do evil.
thanks

---

### Post by nickpaton on 2006-11-18
Install Java and flash using automatix2:

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by nickpaton on 2006-11-18
If you need to, reinstall Firefox via Synaptic, but it shouldn't be necessary.

There are loads of posts in the forums about Java, Flash and Firefox which should be able to help you.

---

### Post by kiyometane on 2006-11-18
I installed automatix with success.
but i cant install some plugins i get thei error in log

"!!SCRIPT OUTPUT END!!
[11/18/2006 - 17:27.29] - ERRORS OR WARNINGS WHERE REPORTED
[11/18/2006 - 17:27.29] - FATAL - Media Players - An apt-based error occured and installation was unsuccessful
[11/18/2006 - 17:27.29] - FATAL - Multimedia Codecs - An apt-based error occured and installation was unsuccessful"


i cant install media player and multimedia codecs.

i was able to install java but some web sites ask me to download java plugins again.
i need help

---

### Post by nickpaton on 2006-11-18
Mmmm never seen that before.

Can you give the following info:

Which distro version?

32 or 64bit distro?

You did download the right version of Automatix for your distro?

---

### Post by kiyometane on 2006-11-18
i downloaded the correct version of automatix. i actually solve te above error. But i still can browse sites that require java and flash even with the automatix update i made.

for ex:
[www.cplus.fr](www.cplus.fr)
[http://speedtest.charter.com/](http://speedtest.charter.com/)

---

### Post by nickpaton on 2006-11-18
Fire up Firefox (close any others down to have only one open).

In the address bar, overtype with the following:

> about:config

Scroll down to the line begining with

> network.dns.disableIPv6

and will probably end with "false".

Click the line to change it to "true".

Close Firefox down (does not need save) and restart.  I don't believe it requires a Dapper restart, but may do.

---

### Post by nickpaton on 2006-11-18
If that doesn't work, then it may be worth upgrading to Flash 9 as per this thread:

[http://ubuntuforums.org/showthread.php?t=279990]("http://ubuntuforums.org/showthread.php?t=279990")

---

### Post by kiyometane on 2006-11-18
Oh i forgot to mention i was using a 64 bit distro.
I dont know if the link you just posted is valid for 64 bit:-k

---

### Post by nickpaton on 2006-11-19
> **kiyometane said:**
> Oh i forgot to mention i was using a 64 bit distro.
I dont know if the link you just posted is valid for 64 bit:-k

There are quite a lot of problems with the 64bit packages which still needs more development.

My Ubu laptop is 64bit and I run the 32bit package very successfully.

People who have made performance comparisons between the two, have reported no discernable difference between them.

Can I suggest that you download the 32bit version, and try that instead.  I think your problems will disappear!

Good luck M8

---

