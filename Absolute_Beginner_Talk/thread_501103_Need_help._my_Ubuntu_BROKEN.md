---
title: "Need help. my Ubuntu BROKEN"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-07-14
Well i tried to install Compiz. But now when i try logging into my gnome session it freezes!! 

And i have no idea what to do. yes i enabled compiz to start up when i log into my session. Is that the problem? Is there a way i can disable that from my failsafe terminal? 


I know all the risks and im not mad, cuz i knew i might mess up, i just want help with out having to reinstall Ubuntu again. And im on Fiesty fawn 

And i need this comp, so any speedy responce is much,much appreciated... Thank you.

---

### Post by mrgnash on 2007-07-14
Shouldn't be a problem, just go into the failsafe terminal and then type:

```
cd ~/.config/autostart
ls
```

You should see the offending startup program (compiz) in there, so just ```
rm
``` it.

---

### Post by w4ett on 2007-07-14
on the login screen there is a button <options> or <sessions> (depending on your particular screen selected)......click on it and select Gnome as your session...it will then prompt you if you want to make it your default...select yes, and boot normally.

---

