---
title: "firefox ver. 1.5.0.8  Java plugin"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by tophatandy on 2006-12-07
Having trouble installing a java plugin on firefox


this is for the old version of firefox(1.5.0.8)..

I was considering updating to 2.0..

so what do you say?..

upgrade and istall the plugin(and if so how would I go about doing it), or install the plugin on the current version (and if so how would I go about doing it)



any help would be greatly appriciated.

:D

---

### Post by dwblas on 2006-12-07
I did a search of the forums on "install java Firefox" and this is one of several links it found.
[http://www.ubuntuforums.org/showthread.php?t=172775&highlight=install+java+firefox](http://www.ubuntuforums.org/showthread.php?t=172775&highlight=install+java+firefox)

---

### Post by tophatandy on 2006-12-07
thats for jre .. updated that almost right away.. I need a plugin to be able to run any javascript in firefox.

---

### Post by tophatandy on 2006-12-07
thanks for the help tho.

---

### Post by tophatandy on 2006-12-10
found the answer in another thread..

here is what I found:


```
sudo aptitude update
```

```
sudo aptitude install sun-java5-plugin
```

this should automatically update firefox's java plugins and add an editors kit to your collection of applications..

(warning this is about 30mb so be carefull if you have a slow internet connection.. could take a while)

hope this thread helps someone..

post if it did..

---

### Post by drphilngood on 2006-12-10
> **tophatandy said:**
> found the answer in another thread..

here is what I found:


Code:```
sudo aptitude update
```

Yes, always remember to update before you install anything, to make sure you are installing the most current version.

---

