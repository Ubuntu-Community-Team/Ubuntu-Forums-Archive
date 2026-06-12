---
title: "Removing evolution got me here - what to do now?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by capricon on 2008-03-03
Recently installed Ubuntu fiesty in my laptop and wanted to remove evolution it because i would not use it. I followed a post here which wanted to use synaptic package manger which i did.
Wherever green was there, it marked for uninstall.(including some packges - i thought it would do the right thing) 

Guess what after all that  i rebooted, did login/password and thats it. **I stay on a blank screen :-(**
Is there any way to goback to be able to use fielsty. (i dont want to reinstall fiesty - which i did already once yesterday).

Thanks.

---

### Post by neurostu on 2008-03-03
yes when you get to the login screen press: CNTRL+ALT+F1 then login, then type:

```

sudo apt-get install evolution

``` 
This will resinstall evolution and all the packages it needs.

---

### Post by RequinB4 on 2008-03-03
In these situations, its really better to use Add/Remove to delete the application for this very reason - you don't want to accidently use synapic to delete packages you need to run the computer :P

---

### Post by capricon on 2008-03-04
> **neurostu said:**
> yes when you get to the login screen press: CNTRL+ALT+F1 then login, then type:

```

sudo apt-get install evolution

``` 
This will resinstall evolution and all the packages it needs.

Thanks. I did it, but still gives me blank Screen right after entering password. - HELP

---

### Post by Joeb454 on 2008-03-04
Did you mark anything to be uninstall called something like ```
ubuntu-desktop
``` I know it sounds strange, but you may have uninstalled some core components of the desktop.

This would explain the lack of a display :)

---

### Post by capricon on 2008-03-04
> **Joeb454 said:**
> Did you mark anything to be uninstall called something like ```
ubuntu-desktop
``` I know it sounds strange, but you may have uninstalled some core components of the desktop.

This would explain the lack of a display :)

Its very well possible. Given that, is there anyway other than re-installing?

---

### Post by nhandler on 2008-03-04
Well, you could type "sudo apt-get install ubuntu-desktop". See if that does anyting.

---

### Post by neurostu on 2008-03-04
also you could try:
```

sudo apt-get install gnome

```

If gnome is still installed nothing will happen, but any packages that gnome needs will be re-installed.

---

### Post by capricon on 2008-03-05
> **Cheater said:**
> Well, you could type "sudo apt-get install ubuntu-desktop". See if that does anyting.

Thanks. That worked.

---

### Post by capricon on 2008-03-05
> **RequinB4 said:**
> In these situations, its really better to use Add/Remove to delete the application for this very reason - you don't want to accidently use synapic to delete packages you need to run the computer :P

But when i tried to remove it thru add/remove it aked me to use synaptic package manager.

---

