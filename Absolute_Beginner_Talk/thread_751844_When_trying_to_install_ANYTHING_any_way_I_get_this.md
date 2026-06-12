---
title: "When trying to install ANYTHING any way I get this message"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by ericxhall on 2008-04-10
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i tried the terminal thing
but it said i could only do it if i had superuser privilages....which confuses me.

---

### Post by NightwishFan on 2008-04-10
Simple, run the command as super user.
```
sudo dpkg --configure -a
```

---

### Post by Mick8882003 on 2008-04-10
Sudo, mean super user, it allows you to do stuff that only root users can do, stops just ne one changing the settings on your comp.

---

### Post by ericxhall on 2008-04-10
ok, so i realized the proble, but now in the updates part...there is one update, i do not want to install, is there any way to clear it?

---

### Post by smartboyathome on 2008-04-10
Unfortunately, no. What don't you want to update? I would say unless you confirmed it is going to break, you should update.

---

### Post by BigFatPapa on 2008-04-11
Not to hijack,  I get the same error code.  I have tried the sudo dpkg --configure -a  and it does not work any help

---

### Post by kesman on 2008-04-11
> **BigFatPapa said:**
> Not to hijack,  I get the same error code.  I have tried the sudo dpkg --configure -a  and it does not work any help

What error message does it give you?

> **ericxhall said:**
> ok, so i realized the proble, but now in the updates part...there is one update, i do not want to install, is there any way to clear it?
Just uninstall the program you don't want to be updated, or select the package in synaptic package manager and mark it as "version locked" state so it won't be updated. What package is it that you don't want to update?

---

