---
title: "Cannot download all repository indexes"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by scorziello on 2007-06-11
Hey guys I am getting the error "Cannot download all repository indexes" every time I use Synaptic Package manager and in the error box it gives me two addresses as follows

[http://ubuntu.beryl-project.org/dists/dapper/main/binary-i386/Packages.gz:](http://ubuntu.beryl-project.org/dists/dapper/main/binary-i386/Packages.gz:) 404 Not Found [IP: 195.114.19.35 80]
[http://ubuntu.beryl-project.org/dists/dapper/main/source/Sources.gz:](http://ubuntu.beryl-project.org/dists/dapper/main/source/Sources.gz:) 404 Not Found [IP: 195.114.19.35 80]

I am fairly new to Linux any help would be great. Thanks

---

### Post by taurus on 2007-06-11
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by waggygee on 2007-06-11
I would guess your using feisty fawn (thats Ubuntu 7.04). Have a look at this [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) It should answer alot of questions

---

### Post by scorziello on 2007-06-11
Thanks I finally was able to access my source list and there was an incorrect line. Every thing is good now thanks for your help

---

