---
title: "MySQL, Apache, Php"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by carternic on 2007-12-10
I'm trying to install MySQl but when I run the configure command I get the response: Configure error: C compiler cannot create executables.

---

### Post by rockinlinux on 2007-12-10
do you have a c compiler installed?

---

### Post by rockinlinux on 2007-12-10
also are you trying to do this on ubuntu server?

---

### Post by akiratheoni on 2007-12-10
> **carternic said:**
> I'm trying to install MySQl but when I run the configure command I get the response: Configure error: C compiler cannot create executables.

You should be able to install MySQL through the Synaptic Package Manager, as well as Apache and PHP, look for it there. But anyway, use this command:

```
sudo apt-get install build-essential
``` to download the ability to compile from source.

---

### Post by hyper_ch on 2007-12-10
why do you want to compile it and why don't you install it from apt?

---

### Post by saj0577 on 2007-12-10
[http://www.howtoforge.com/ubuntu_lamp_for_newbies]("http://www.howtoforge.com/ubuntu_lamp_for_newbies")

That might help.

Saj

---

### Post by indytim on 2007-12-10
$tasksel

IndyTim

---

### Post by carternic on 2007-12-12
Hi, thanks for you replY. Checked and have compiler but missing a library. Sorted that now need something else. will get there eventually! 

This is for 'not for profit' org in central Africa, no internet connection exceptweekly on dial-up takes a day, round trip. Need to build set of cd's to load system and app's etc before I leave. Would also like to paid for past year's work! Long story.

---

### Post by carternic on 2007-12-12
Hi, Site in Central Africa for 'non-profit org' has no internet access. only once per week on internet cafe dial-up line v unreliable plus full days journey away. Need to build install for sys, apps etc from cd's.

---

### Post by hyper_ch on 2007-12-12
maybe you should get an Ubuntu DVD. Most repositories and stuff is on there. Just updates would be required.

---

