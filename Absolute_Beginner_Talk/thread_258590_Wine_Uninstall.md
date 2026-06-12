---
title: "Wine Uninstall"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by srusso on 2006-09-16
Hey everyone I have Wine installed on my system though Automatix needless to say I messed it up and I want to completely remove it. And install the leastest build... Also I am possibly looking for something easier wine, maybe a little more user friendly? Or if anyone knows a great wine tutorial site and a place to noob learn how to use wine correcty. :confused:

---

### Post by arnieboy on 2006-09-16
> **srusso said:**
> Hey everyone I have Wine installed on my system though Automatix needless to say I messed it up and I want to completely remove it. And install the leastest build... Also I am possibly looking for something easier wine, maybe a little more user friendly? Or if anyone knows a great wine tutorial site and a place to noob learn how to use wine correcty. :confused:

AX installs the latest version of wine from official wine repositories. To remove it do the following:
```
sudo apt-get remove wine
sudo rm -rf ~/.wine
```
The AX team will update Bleeder later today and it will carry an easy graphical tool to configure and install stuff in wine. If you have the AX repositories added, you will get it as an update later today.

---

### Post by Najand on 2006-09-16
Why you don't use Wine documentations at [www.winehq.com/](www.winehq.com/) .

---

### Post by arnieboy on 2006-09-16
> **Najand said:**
> Why don't you talk this issue in Automatix forum, as it is not a general ubuntu issue but an automatix issue?

Its not an AX issue either.. but anyways.

---

