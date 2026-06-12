---
title: "Dependencies and installing Programs."
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Horsman on 2006-06-25
When I try to install most packages (like say build-essential or gcc) it always says there are other packages its dependant on. EG:

I try to install glade-gnome2 : need gnome-common : which needs libtool : which needs cpp etc etc.

How can I get around this?

---

### Post by aysiu on 2006-06-25
Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Kilz on 2006-06-26
[QUOTE=Horsman]When I try to install most packages (like say build-essential or gcc) it always says there are other packages its dependant on. EG:

I try to install glade-gnome2 : need gnome-common : which needs libtool : which needs cpp etc etc.

How can I get around this?[/QUOTE]
Use synaptic, or 
sudo apt-get install <packagename>
It should also install the packages that are needed.
If you are asking how you can avoid installing packages the one you are installing needs, I done recommend that. Your system wuld become unstable.

---

### Post by Horsman on 2006-06-26
No luck, it babbled on and then said not installign would resolve the dependancies.

---

### Post by aysiu on 2006-06-26
Instead of a summary, can you post the actual error messages?

---

