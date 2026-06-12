---
title: "compiz broke and now i cant intsall and get it to work!!"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by searayman on 2007-04-11
mike@mike-desktop:~$ sudo apt-get install compiz compiz-gnome
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins but it is not going to be installed
          Depends: compiz-decorator
  compiz-gnome: Depends: compiz-core (= 1:0.3.6-0gandalfn11) but 1:0.5.0-1~3v1ubuntu1 is to be installed
E: Broken packages
mike@mike-desktop:~$

---

### Post by troymcdavis on 2007-05-06
What version of Ubuntu are you using? It comes installed with Feisty, you just have to enable it.

---

