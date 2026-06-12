---
title: "How do you start XFCE?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by roxics on 2006-07-07
I just installed Xubuntu on an older machine in OEM mode. I think that was the way I wanted to install it. Anyway everything went fine but when the computer restarts it goes straight to a command line. How do I get it to start up in the XFCE interface everytime?

---

### Post by bruce89 on 2006-07-07
What actually happens, is there a warning about how X didn't start up?

---

### Post by roxics on 2006-07-07
No warning. It jsut asks me to login as username "oem" with the password I selected during setup and then just gives me a prompt that doesn't have administrative control. 

I tried typing "startx" and it tells me it's a bad command.

So now I'm just reinstalling it in non oem mode, maybe that will help.

---

### Post by aysiu on 2006-07-07
You need a display manager like *wdm* or *gdm*. ```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm restart
``` **Edit**: Oh, so even *startx* doesn't work. Then you're having weird X issues...

---

### Post by bruce89 on 2006-07-07
Mabye Xubuntu didn't install completely (did you do a server install?)
```
sudo aptitude install xubuntu-desktop
``` will install it completely.

---

### Post by CREEPING DEATH on 2006-07-07
I had the same problem with Xubuntu before, I think it might be a problem with the OEM install process.

Jeff

---

### Post by xael on 2006-07-07
> **bruce89 said:**
> Mabye Xubuntu didn't install completely (did you do a server install?)
```
sudo aptitude install xubuntu-desktop
``` will install it completely.

Just a little addition to the previous comment: before using Aptitude, remember to update it first, then use it to install the package you desire. It works much better that way. 8)

---

### Post by roxics on 2006-07-07
Thanks guys, but I just did a reinstall. 

There is no standard install option on the CD menu. But I read the help file and it told me how to do a standard install from the boot screen, so I reinstalled it and everythign is working fine. I just don't know what the password is for the administrator. Is there a default?

---

