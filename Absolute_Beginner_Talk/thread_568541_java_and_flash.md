---
title: "java and flash"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by sp0onman on 2007-10-05
hi i am having some trouble finding a guide to install the latest flash and jave, cna somebody point me in the right direction?

---

### Post by FuturePilot on 2007-10-05
I'm not exactly sure about Java, I always just use what ever the latest version in the repos is.
As for Flash the latest should be in the repos. But if you're talking about the Flash 9 Beta one then just download the archive and extract it. Then open a terminal and cd into the directory it was extracted to.
Type ```
sudo ./flashplayer-installer
```
That will install it system wide. Enter 
```
/usr/lib/firefox
```
when it asks you for a browser directory.
Or if you would rather install it only for your account, just run the installer without sudo

---

### Post by Sef on 2007-10-06
applications > Add/Remove

They are both there.  

Sun Java 6  (select the top one.)

Adobe (select the top one.)

---

### Post by Seisen on 2007-10-06
You need to enable the Mulitverse Repository otherwise you won't find them when you search for them.

---

### Post by Sef on 2007-10-06
> You need to enable the Mulitverse Repository otherwise you won't find them when you search for them.

With Add/Remove, change the top right box to 'All Available Applications'.

---

