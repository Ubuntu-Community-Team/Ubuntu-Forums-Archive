---
title: "Need help With the Emerald Theme Manager"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-31
I am trying to get [this Emerald Theme]("http://gnome-look.org/content/show.php/Vista-Linux?content=42875") working. I installed the Emerald Theme Manager with:

```
sudo apt-get install emerald
```

I downloaded the theme file from GNOME-Look.org and opened it up with the Emerald Theme Manager. So far so good. It is not just sat in the window, I don't know how to activate it. Double clicking on it doesn't do anything. I am running Compiz Fusion with it set to 'Extra' through Ubuntu. How do i get it to actually do something? Thanks.

[[IMG]http://img233.imageshack.us/img233/3264/screenshot1dx7.th.png[/IMG]](http://img233.imageshack.us/img233/3264/screenshot1dx7.png)

---

### Post by LowSky on 2008-01-31
hope this helps... go into terminal and type
```
emerald --replace
```
this should so it

see this link for more help

[http://ubuntuforums.org/showthread.php?t=510363](http://ubuntuforums.org/showthread.php?t=510363)

---

### Post by Crumpets and Jam on 2008-01-31
> **LowSky said:**
> hope this helps... go into terminal and type
```
emerald --replace
```
this should so it

see this link for more help

[http://ubuntuforums.org/showthread.php?t=510363](http://ubuntuforums.org/showthread.php?t=510363)

Thanks. How would I revert back to the original?

---

### Post by LowSky on 2008-01-31
```
metacity --replace
``` or ```
compiz --replace
``` depending on your settings

---

### Post by Crumpets and Jam on 2008-01-31
> **LowSky said:**
> ```
metacity --replace
``` or ```
compiz --replace
``` depending on your settings

Thanks, man.

---

