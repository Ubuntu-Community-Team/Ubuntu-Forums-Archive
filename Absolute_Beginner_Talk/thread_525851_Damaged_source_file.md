---
title: "Damaged source file"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by canfrank on 2007-08-14
I am running Ubuntu 7.04., while installing my printer I deleted the content of my source list. Now my update manager is not working anymore. How can I create a new source list, since everything in the old one is gone?

---

### Post by ThrobbingBrain66 on 2007-08-14
```
## Main & Restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Universe & Multiverse                                                   
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse universe 

## Bug Fixes
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe

## Backports
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse universe 

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe
```

Just paste that into your sources file and 'sudo apt-get update'

---

### Post by Blutack on 2007-08-14
Have his, its neater

---

