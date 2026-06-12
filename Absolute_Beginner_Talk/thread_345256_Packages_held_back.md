---
title: "Packages held back??"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by andrew.46 on 2007-01-24
Hi,

 I upgraded from Xubuntu Dapper to Xubuntu Edgy a few days ago using apt-get and following instructions on:

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

 All has gone well and I am very happy with Edgy. But some packages have been held back:

```
andrew@Troy:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  hpijs update-manager xubuntu-desktop
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```
I am not unduly worried: my system is running well but I am more than a little curious as to what is going on here. Can anyone help?

                     Andrew

---

### Post by ashmew2 on 2007-01-27
Have u tried running the Update manager before dist-upgrade ? Run the update Manager and update your system and try that again. I am pretty sure that when it says something like " The following packages have been kept back" , it is referring to the Update Manager :)

---

### Post by bruenig on 2007-01-27
Has nothing to do with the update manager. Try sudo apt-get installing each of those things separately. That is what I usually do on the rare occasion when I get that. Also, I use sudo apt-get upgrade not dist-upgrade. Not sure if that makes too big a difference, but worth a shot.

---

