---
title: "Trying to upgrade from Dapper Drake to Edgy Eft I get this,any assistance appreciated"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ebony_rogue on 2007-06-01
jeanjimbo@Jimbo-PC:~$ gksu 'update-manager -c'

(gksu:6355): Gdk-WARNING **: locale not supported by Xlib

(gksu:6355): Gdk-WARNING **: cannot set locale modifiers
(update-manager:6356): Gdk-WARNING **: locale not supported by Xlib

(update-manager:6356): Gdk-WARNING **: cannot set locale modifiers
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
jeanjimbo@Jimbo-PC:~$





From here I get the update manager but no option to upgrade to Edgy Eft, instead I get :
"Your system is up to date "

---

### Post by bobplano on 2007-06-01
i think you need to do 
```
gksu update-manager -c -d
```
or something similiar

---

### Post by zvacet on 2007-06-01
Change your sources list from Dapper to Edgy

```
 sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

```
sudo aptitude update
```

---

