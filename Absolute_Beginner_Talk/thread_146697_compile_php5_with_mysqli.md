---
title: "compile php5 with mysqli"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by rcpettit on 2006-03-18
I need php5-mysqli which isn't in the repository.  I downloaded the php5 source from the repository but I don't see where to make the changes  so it builds the module.  I've looked on the web and here  for  a how to  but  every one I found only talks about building the package but not where to make the changes.   I know I can use mysqli from dotdeb.org but I want to stay with the ubuntu packagaes as much as possible. I'm new to working with debs so don't flame me too bad. :)

---

### Post by FizDev on 2006-03-18
Well, I don't think there should be a problem using those from dotdeb.org as Ubuntu is based on Debian so...

To install it, just do :
```
sudo gedit /etc/apt/sources.list
```
then add these lines at the end of sources.list then save.
> deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
deb-src [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all

```
sudo apt-get update
```
```
sudo apt-get install php5-mysqli
```

---

### Post by dudus on 2006-03-22
There is a how to compile php5 with mysqli support:

[https://wiki.ubuntu.com/PHP5FromSource]("https://wiki.ubuntu.com/PHP5FromSource")

---

