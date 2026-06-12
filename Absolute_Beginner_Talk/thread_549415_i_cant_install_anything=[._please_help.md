---
title: "i cant install anything=[. please help"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by russo1324 on 2007-09-12
O lord. 

Hello everybody. 

well after installing the ubuntu studio audio package from the repository( im using feisty fawn btw), i decided to install WINE so i can use other simple windows apps.

i tried and i got this message...along with any other install i tried after.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


.... now i installed just the package nd plugins because i knew i needed some good free audio software. but i didnt have the time or money to get full version of ubuntu studio......maybe that has something to do with it?

any ideas and help would be greatly appreciated..

Thanks=]

-danny

---

### Post by stchman on 2007-09-12
> **russo1324 said:**
> O lord. 

Hello everybody. 

well after installing the ubuntu studio audio package from the repository( im using feisty fawn btw), i decided to install WINE so i can use other simple windows apps.

i tried and i got this message...along with any other install i tried after.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


.... now i installed just the package nd plugins because i knew i needed some good free audio software. but i didnt have the time or money to get full version of ubuntu studio......maybe that has something to do with it?

any ideas and help would be greatly appreciated..

Thanks=]

-danny

Here is how you install WINE in Feisty:

[http://www.stchman.com/install_wine_IE.html](http://www.stchman.com/install_wine_IE.html)

Pay attention to the Install WINE portion.

---

### Post by overdrank on 2007-09-12
> **russo1324 said:**
> O lord. 

Hello everybody. 

well after installing the ubuntu studio audio package from the repository( im using feisty fawn btw), i decided to install WINE so i can use other simple windows apps.

i tried and i got this message...along with any other install i tried after.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


.... now i installed just the package nd plugins because i knew i needed some good free audio software. but i didnt have the time or money to get full version of ubuntu studio......maybe that has something to do with it?

any ideas and help would be greatly appreciated..

Thanks=]

-danny

Hi you can run that command 
```
sudo dpkg --configure -a
```
In the terminal located under applications, accessories, terminal and don't panic when you see your password not showing when typed. Good luck

---

### Post by mlentink on 2007-09-12
I don't really think I understand your question. Why would you spend money for Ubuntu Studio?
Why didn't you simply install Wine from the repositories?

---

### Post by Matt Yun on 2007-09-12
> **russo1324 said:**
> 
well after installing the ubuntu studio audio package from the repository( im using feisty fawn btw), i decided to install WINE so i can use other simple windows apps.

i tried and i got this message...along with any other install i tried after.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



See:  [Ubuntu Community Documentation on Adding, Removing and Upgrading Applications]("https://help.ubuntu.com/7.04/add-applications/C/index.html").

The easiest way to install WINE is through the "Add/Remove..." tool in the Applications menu (it's the item at the very bottom).  Search for "Wine", check the box for "Wine Windows Emulator" and then click the "Apply" button.

You should be warned, however, that WINE is not for the faint of heart.  You should thoroughly google whether your "simple windows apps" work with WINE.  Take a look at [http://frankscorner.org](http://frankscorner.org) and [http://www.winehq.org](http://www.winehq.org)

---

