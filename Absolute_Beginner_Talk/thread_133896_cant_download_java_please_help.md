---
title: "cant download java please help"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by red73 on 2006-02-20
i try to click on it it says open or save to disk. i try to save it and nothin happens.can someone help me ......im new to ubuntu and really want to learn it thanx

---

### Post by akiro.yamamoto on 2006-02-21
Are you trying to download the Sun Java package from the Sun website?
Can you give a little more info?
Try this, it's a link to the Sun Java .bin Download
[http://jdl.sun.com/webapps/download/AutoDL?BundleId=10335](http://jdl.sun.com/webapps/download/AutoDL?BundleId=10335)
Just save to disk, it should work.

---

### Post by Perfect Storm on 2006-02-21
Another way (only works with x86 stucture):

```
sudo gedit /etc/apt/sources.list
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/b]

```
sudo apt-get update
sudo apt-get install sun-j2re1.5
```

---

