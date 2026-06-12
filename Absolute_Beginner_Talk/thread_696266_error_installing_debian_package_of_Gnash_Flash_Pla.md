---
title: "error installing debian package of Gnash Flash Player"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by RoBo5050 on 2008-02-13
Hello forum members,
  I am having great difficulty installing Gnash Flash Video Player with the GDebi Package Installer on Ubuntu 7.10;every time I try to open the package installer I get the following error message:"Error: dependency is not satisfiable: libgnash0"!!
 I would like to know how to install this package without getting this error message again ,,or a workaround to  this problem??:confused:

Thanks in advance for a reply to this "newbies" question!!

---

### Post by jw5801 on 2008-02-13
That means you need the "libgnash0". If you install gnash via synaptic, then it will take care of any dependecies for you. gnash is in the repositories so you can install it with:
```
sudo apt-get install gnash
```Or by finding it and checking it for installation in synaptic.

---

### Post by KCormier on 2008-02-13
I personally don't like gnash.  If you're trying to add swf, wma, wmv support and the like i recommend opening a console and running 

```
sudo apt-get install ubuntu-restricted-extras
```

This takes care of a whole host of extras from java, to ms fonts, to wma, wmv, and swf support.  :)  It's the first thing i do on new ubuntu installs!

---

